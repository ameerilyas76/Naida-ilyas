# Clearence Document Arco:

- Setup (Entity)
- Factors (Entity)
- Equation (Created for Components)

- Components (All the componants to calculate clearance, Entity, Like Activity, will be assigned to Calculation or Active/Deactive in a Seperate list)
- Calculation (Entity, like Case)

# Clearance Type
-Retirement
-Vacation
-End Contract

# Clearance Type Component Assignment

### Clearance Request
- Clearance Amount= Due Salaries – Cost of Food +Ticket – Deducted Loan +Other Payment – Other Deduction + Vacation Amount + EOS Amount – Gov. & Agency Fees.

### Clearance Request will be created from 
1) Retirement Request
2) Leave Request
3) Business Contract

### Clearance Request Stages
- Review
- Approval
- Under Processing
- Complete
- Cancel Requested
- Cancelled

### Once the clearance reaches to the Under Processing stage, one of the following documents will be generated as was explained previously: 
1. Final settlement 
2. Vacation settlement 
3. Non-Monthly Invoice.

# clearance cancellation 

### Once the clearance cancellation reaches to the approved stage, the following Actions will be done: 
1. Creates loan in “Complete” stage. 
2. Cancels the vacation settlement if it has been generated. 
3. Cancels the retirement settlement if it has been generated. 
4. Creates credit note if non-monthly invoice has been generated and the employee will return to the same contract.


# 1)Business Contract - Add new system action” End Contract”.
Create retirement request by “End contract” action for all reasons except “Escape” and “Not Return from Vacation”
Integration between the BS Contract and Clearance:The integration depends on the calculation method at the contract.
The system will create “Clearance Calculations” automatically when return employee to “Lodging” or “Customer” and complete the relevant data based on the clearance setup.

# 2)Non-Monthly Invoice will be created when the clearance request reaches the invoice stage
If the invoice is generated from clearance, once the invoice reaches to approved stage, the clearance will move to the “Complete” stage.

# 3)Credit note may be generated from:
when Cancel the clearance, if non-monthly invoice is created and the employee will return to the same contract, Create credit note for the customer for the same amount of invoice.
when clearance paid by customer is selected in the Clearance Setup
The system will create non-monthly invoice and credit note for the customer, amount is the clearance amount
Link the Credit note to the non-monthly invoice

# 4)Retirement Request will be created automatically
4.1) business contract - when applying end contract action on an employee, retirement request will be created in “Draft” stage.
4.2) Individual contract - when the contract reaches to “End with Transfer” stages, the reason is “Employee Transfer”
4.3) Retirement Request will be created as soon as the employee “Status in Moqueem” changed to specific statuses, (Escape,Left Not Returned,Dead)
4.4) When the retirement request reaches to “Under Processing” stage, creates clearance request

# 5)HRM>Employee Retirement>Final Settlement
• Remove “Calculate Amount” Option.
• Stop generating final settlement from the retirement request.
• Final settlement will be generated by the clearance.
• A new workflow stage “Cancelled” will be added.
• In case the clearance type is vacation and final exit or final exit only and clearance reaches to “Cancelled” stage, move the final settlement to “Cancel” stage too.
• Final settlement will generate non-monthly invoice and credit note when reaches to the “Client Confirmation” stage, as will be explained later.
• Final Settlement will be not generated if the clearance type is “Final Settlement” or “Final Settlement and Vacation”, and the reason is “Escape” or “Not Return from Vacation”

# 6)Leave Request:
6.1) When the Leave request reaches to “Under Processing” stage, creates clearance request
6.2) Show the employee’s loan balance at the leave request.

# 7)HRM>Leave Management>Vacation Settlement:
HRM>Leave Management>Vacation Settlement:
• Remove “Calculate Amount” Option.
• Stop generating vacation settlement from the leave request.
• Vacation settlement will be generated by the clearance.
• When clearance reaches to “Approved” stage, will generate a “Vacation Settlement”.
• A new workflow stage “Reserved” will be added.
• In case the clearance type is vacation only and vacation amount marked as “Reserved”, the vacation settlement after the “Client Confirmation” stage, will be moved to “Reserved” stage instead of the “Payment” stage.
• A new workflow stage “Cancelled” will be added.
• In case the clearance type is vacation only and clearance reaches to “Cancelled” stage, move the vacation settlement to “Cancel” stage too.
• When the employee return from vacation, move the settlement to the “Payment” stage and create the payment request and complete the cycle as usual.
• Integration between the “Vacation Return” and “Vacation Settlement” is needed.
• Vacation settlement will generate non-monthly invoice and credit note when reaches to the “Client Confirmation” stage, as will be explained later.

# 8)HRM>Leave Management>Vacation Return:
• Integration between the “Vacation Return” and “Vacation Settlement” is needed • Once the “Vacation Return” moved from “Waiting for Return” stage to “Complete” stage, move the “Vacation Settlement” to the “Payment” stage.
Return ticket is paid when the employee return from his vacation.

# 9) Loan 
1. The whole loan will be deducted if the clearance type is “Final Exit”.
2. May deduct loan partially if clearance type is “Vacation” only, and Re-schedule the remaining amount of the loan.
3. Will be not calculated if the clearance type is “Return Employee”.


# 10)HRM>Finance>Payment Setup
Add new two fields for “Period” and “Period Type”(Day, Week, Month, Year).

# 11)PRL>Accrual Setup> Provision Flight Ticket
1. Change the page name to be “Flight Ticket”.
2. Change the title of “New” and “Edit” Pop-Ups to be “Flight Ticket”.

# 12)HRM>Finance> Payment Request
• Adding a new column for “Payment Date”.
• That column displays the actual payment date of all payment requests (Iqama, MOL, ATM…etc.).

# 13)HRM> Employee >Employee List:
Retirement Request will be created as soon as the employee “Status in Moqueem” changed to specific statuses, as the following:

# 14)HRM> Employee >Employee Inquiry:
• The “Retirment Reason” at the “Retirement Request” should reflect in the” Contract Status” at the “Employee Inquiry” page.
• When the “Retirement Request” reaches to the “Complete” stage, update the “Contract Status” at the “Employee Inquiry” page.

# 15)ERP> Individual Contract:
Create “Retirement Request” as soon as the individual contract reaches to “End with transfer” stage.


when request LEave and Retirement, we need to start the settlement always and get the approval from the finance department, and if the user wants the settlement payment (check box in the request) the request will be going to all the stages including cusomer approval and payment, otherwise it will be  completed after the finnce approval
