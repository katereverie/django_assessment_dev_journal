# 1. Performance issue on Admin appointment list view

## Task Description

The appointment list admin is slow to load. <br>
Find out why and fix the performance issue. <br>
Note that you have the django debug toolbar installed.

## My Approach

I've gone through the official tutorial of Django (until part 8 where I learned to install Django debug toolbar).<br>
So, I've learned how to install Django debug toolbar, but I have little idea about how to use it appropriately.<br>

### Problem decomposition

#### Analysis

1. Since this task requires fixing a specific performance issue - slow loading speed -, I first ran the server and tested it out manually to see how 'slow' it actually is.
2. Since 'slow' is rather subjective, I did not feel that loading the appointment list was particularly slow. So, manually testing was not help.
3. Since manually testing is no help, I need some objective measurement to measure the loading speed.
4. So, I need to first figure out how to measure loading speed of this specific action - loading appointment lists.
5. I checked `Profiling', nothing obvious happened on the UI, so I turned to terminal messages/logs

Here's a list of logs:

```
[07/Oct/2024 09:26:09] "GET / HTTP/1.1" 200 14118
Not Found: /admin/polls
[07/Oct/2024 09:26:15] "GET /admin/polls HTTP/1.1" 404 18333
[07/Oct/2024 09:26:23] "GET /admin/ HTTP/1.1" 200 24481
```
Clicking on `Appointments`
```
[07/Oct/2024 09:27:46] "GET /admin/core/appointment/ HTTP/1.1" 200 74156
[07/Oct/2024 09:27:46] "GET /admin/jsi18n/ HTTP/1.1" 200 3342
```
Since nothing informative about performance issue due to a lack of objective measurement, I decided to consult with ChatGPT to on how to measure loading speed.

6. steps I followed from there:
   - Clicked on Profiling and checked the panel, `CUMTIME`: cumulative time spent in the function and all functions it called, so if the CUMTIME of calling a function is particularly high compared to other function calls, it indicates this is causing the performance overhead.

![Screenshot 2024-10-07 100844](https://github.com/user-attachments/assets/4fccd3d0-ea2b-434a-87f7-df0c0f998d37)

It's obvious from the first call that 

- Nested calls: The nested structure suggests there's a recursive or deeply nested call pattern occurring, primarily involving __exception handling__ and __deprecation warnings__. This could be causing unnecessary overhead.
- Repeated calls: Several functions are being called multiple times, particularly in the django.core.handlers.exception and django.utils.deprecation modules. This repetition may be contributing to the slow loading time.
- Total time: The cumulative time (CUMTIME) for the top-level call is 0.836 seconds, which is significant for a single page load.

   - checked SQL to see if there are inefficient SQL queries. This may be important because if there's a large amount of data, you'd only want the data you need for appointment list.
      - The issue is likely occurring because your AppointmentAdmin class is set to pass, which means it's using all the default behaviors. In this case, it's probably trying to display related fields for each appointment individually, resulting in separate queries for each appointment.
      - I suspected it has something to do with inefficient database queries because I clicked open the SQL panel and saw "100 similar queries || duplicated 100 times".
      - Found out that `AppoinmentAdmin` is set to pass. Did some quick research and found out that if default behaviors are applied if set to pass, which is very inefficient.
      - So I implemented AppointmentAdmin with several features and optimized database queries.
