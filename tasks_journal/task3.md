# Overview Task 3

## __Appointment detail view__

Add a detail view for the appointment model. This view does not exist yet, so you'll have to create it from scratch. <br>
We don't really care for optics, in fact we only included pico.css so that the page looks somewhat nice.<br>

The detail view should allow you to edit and delete the appointment.

## Steps

1. created detail view in views.py
2. added URL route in urls.py
3. created the appointment detail template under '/core/templates/core'
4. refactored index view to include a link to detail view
5. committed changes
6. noticed loading index view takes too long.
7. added pagination to index view and index.html
8. fixed update issue (no update) by formating date as DD.MM.YYYY to fit into HTML-friendly date format
9. chanegd form layout, added some simple styles using Pico
10. fixed update issue (updating customer and employee not reflected in changes) by using `get_or_create()`
    - This is an issue with my unfamiliarty with Djangp (must deep dive)
11. simplified __str__ method to return customer and employee name directly (probably trivial)
12. moved back link, h2 to the middle

## Demos: index view and detail view

Index:

![indexviewnow](https://github.com/user-attachments/assets/63cb285d-654c-4f52-bc53-24ad642adb1c)

Detail:

![detailviewnow](https://github.com/user-attachments/assets/f22bb698-e203-423e-8175-db9944e85a6e)
![Screenshot 2024-10-08 193302](https://github.com/user-attachments/assets/e87726db-5fe6-4401-84a3-ff3e57b9dcc1)
