# 6. Filter appointments by customer and employee

## Task Description

Add a filter to the list view to only show appointments for a specific customer or employee.

## Steps

1. Created the filter form:
   - Added AppointmentFilterForm in forms.py.
   - Included dropdown fields for employee and customer using ModelChoiceField.
   - Made both fields optional (required=False).
2. Updated the index view:
   - Modified index view in views.py to handle filter form logic.
   - Added check for the "reset" button to clear filters when clicked.
   - Applied filter conditions if form is valid (filtered appointments by selected employee and/or customer).
   - Passed the form and filtered appointments to the template context.
3. Updated the index template:
   - Added filter form to index.html with employee and customer dropdowns.
   - Created a filter button (Filtern) and a reset button (Zurücksetzen).
   - Styled the form using a grid layout, aligning the buttons with the dropdowns.
4. Refactored pagination:
   - Simplified pagination in index.html for a cleaner, German-style format.
   - Improved accessibility by using aria-label on pagination links.
   - Used request.GET.urlencode to retain filter parameters in pagination links.
   - Replaced traditional text-based pagination with symbols "«" and "»" for better UX.
     
![Screenshot 2024-10-09 094311](https://github.com/user-attachments/assets/078f6f4f-26e9-4229-a15c-b3e28e40bd39)
