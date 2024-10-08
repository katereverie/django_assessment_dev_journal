# Render appointments on the index page

## Task Description

The index page should render a list of all appointments, with required information (see table in index.html). Adjust the view ("core.views.index") and template ("core/index.html") accordingly.

Bonus: add pagination, so that large amounts of appointments are not rendered at once.

## Observation & Things I did

Notes:
1. The index page is at the root. Since no domain name, the base address is: "http://127.0.0.1:8000/"
   
![indexpageUI](https://github.com/user-attachments/assets/64480dc8-8940-41c7-85a6-befcd4bbad80)

Steps:
1. noticed a missing closing tag of `<tbody>`, so I added a `/` to the closing tag
2. adjusted the index view
3. adjusted the template
4. ran server to check rendered view
5. Under 'Kunde' and 'Mitarbeiter', saw redundant information, ex: `Kunde "Katharian Karakus"` instead of simply "Katharina Karakus".
6. refactored `Customer` and `Employee` models to only return the name field without any other string texts
7. ran server to check updated rendered view. No issue.
8. committed each change with appropriate messages
9. moved pagination to the middle
![Screenshot 2024-10-07 114543](https://github.com/user-attachments/assets/f1a212ab-2c4a-4b09-96d6-ce2a8e38667b)
