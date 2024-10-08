# Overview 

## 5. Add a new appointment

From the list view (index.html), add a button to create a new appointment.

## Steps & other related commits

1. added a button for adding new appointment to the list view, at the bottom right
2. refactored list view (index.html) for better UX (still kinda sucks)
3. created new HTML template for adding appointments
4. refined appointment creation form layout and styling
5. implemented 'add_appointment' view function with form processing and error handling
6. added URL route '/add/' for the new appointment creation page
7. updated 'Add Appointment' link in main template to use correct URL
8. refactored pagination to show 15 appointments per page
9. fixed date format inconsistency in index
10. refactored index view to order appointments by date
11. added a button for adding appointment in index
12. added employee dropdown to 'add_appointment' page
13. fixed employee section issue in add_appointment view
14. updated employee dropdown in detail view
15. fixed issue with empty value in employee dropdown
16. refactored detail view to fectch employee by ID, avoiding creating new employee
