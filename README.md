# OdooOrbit
Team OdooOrbit


## Phase 1: Setup & Configuration (Admin Role)
First, you need to set up the users and the approval rules.

Log in as the Administrator.

Create Test Users: Navigate to Settings > Users & Companies > Users.

Create a "Manager" User:

Name: Test Manager 👨‍💼

Role: Set to Manager.

Manager: Leave blank.

Is Manager Approver: Check this box. This is crucial for testing the "manager first" logic.

Create an "Employee" User:

Name: Test Employee 👩‍💼

Role: Set to Employee.

Manager: Select Test Manager.

Create an Approval Rule:

Go to the Expenses app.

Navigate to the menu Approval Rules > Approval Rules.

Create a new rule named Standard Approval.

Under the Approver Sequence tab, add a line and select your Administrator user. Set the sequence to 10. This creates a two-step flow: first the employee's manager, then the admin from this rule.

## Phase 2: Employee Submits an Expense
Now, act as the employee submitting a claim.

Log out from Admin and log in as Test Employee.

Create an Expense:

Go to Expenses > My Expenses and create a new expense.

Description: Client Lunch Meeting

Amount: 150

Save the expense. The status will be Draft.

Submit the Expense:

Click the Submit to Manager button.

Verification: ✅

The status should now be Submitted.

Check the Current Approver field. It should now show Test Manager.

Click on the Approval Process tab. You should see two lines: one for Test Manager (Status: Pending) and one for your Administrator (Status: Pending).

## Phase 3: Manager Approves the Expense
Next, perform the manager's part of the workflow.

Log out and log in as Test Manager.

Find the Pending Expense:

Go to Expenses > Approvals > Expenses to Approve. You should see the Client Lunch Meeting expense from Test Employee.

Approve It:

Open the expense. You should see the Approve and Reject buttons.

Click Approve.

Verification: ✅

The Current Approver field should now change from Test Manager to your Administrator user.

In the Approval Process tab, the status for Test Manager should now be Approved.

To complete the flow, you would now log in as the Administrator, find the expense in "Expenses to Approve," and give the final approval. The expense status will then change to Approved.

## Phase 4: Testing Conditional Rules
This is to test the more complex logic from your approval_rule.py file.

Setup: As Admin, create a third user, Finance User (Role: Manager). Modify your Standard Approval rule and add both the Administrator and Finance User to the Approver Sequence. You now have 3 total approvers for any expense (Manager, Admin, Finance).

Scenario A: Percentage Rule (60% Required)
Configure Rule: Set Approval Percentage Threshold to 60 and make sure Hybrid Rule is unchecked.

Submit Expense as Test Employee.

First Approval: Log in as Test Manager and Approve. (1 of 3 approved = 33%). The expense should remain Submitted, and the current approver should change to the next in line.

Second Approval: Log in as Finance User and Approve. (2 of 3 approved = 66%).

Verification: ✅ As soon as the second approval happens, the expense status should automatically change to Approved because the 60% threshold has been met.

Scenario B: Specific Approver Rule (Admin is Key)
Configure Rule: Set the Specific Approver field to your Administrator user. Uncheck Hybrid Rule.

Submit Expense as Test Employee.

First Approval: Log in as Test Manager and Approve. The expense remains Submitted.

Second Approval: Log in as Administrator and Approve.

Verification: ✅ The moment the Administrator approves, the expense status should immediately change to Approved, regardless of the percentage.

## Phase 5: Testing Rejection
Submit a new expense as Test Employee.

Log in as Test Manager.

Find the expense in "Expenses to Approve" and click Reject.

Verification: ✅ The expense status should immediately change to Refused, and the approval process should stop completely.## Phase 1: Setup & Configuration (Admin Role)
First, you need to set up the users and the approval rules.

Log in as the Administrator.

Create Test Users: Navigate to Settings > Users & Companies > Users.

Create a "Manager" User:

Name: Test Manager 👨‍💼

Role: Set to Manager.

Manager: Leave blank.

Is Manager Approver: Check this box. This is crucial for testing the "manager first" logic.

Create an "Employee" User:

Name: Test Employee 👩‍💼

Role: Set to Employee.

Manager: Select Test Manager.

Create an Approval Rule:

Go to the Expenses app.

Navigate to the menu Approval Rules > Approval Rules.

Create a new rule named Standard Approval.

Under the Approver Sequence tab, add a line and select your Administrator user. Set the sequence to 10. This creates a two-step flow: first the employee's manager, then the admin from this rule.

## Phase 2: Employee Submits an Expense
Now, act as the employee submitting a claim.

Log out from Admin and log in as Test Employee.

Create an Expense:

Go to Expenses > My Expenses and create a new expense.

Description: Client Lunch Meeting

Amount: 150

Save the expense. The status will be Draft.

Submit the Expense:

Click the Submit to Manager button.

Verification: ✅

The status should now be Submitted.

Check the Current Approver field. It should now show Test Manager.

Click on the Approval Process tab. You should see two lines: one for Test Manager (Status: Pending) and one for your Administrator (Status: Pending).

## Phase 3: Manager Approves the Expense
Next, perform the manager's part of the workflow.

Log out and log in as Test Manager.

Find the Pending Expense:

Go to Expenses > Approvals > Expenses to Approve. You should see the Client Lunch Meeting expense from Test Employee.

Approve It:

Open the expense. You should see the Approve and Reject buttons.

Click Approve.

Verification: ✅

The Current Approver field should now change from Test Manager to your Administrator user.

In the Approval Process tab, the status for Test Manager should now be Approved.

To complete the flow, you would now log in as the Administrator, find the expense in "Expenses to Approve," and give the final approval. The expense status will then change to Approved.

## Phase 4: Testing Conditional Rules
This is to test the more complex logic from your approval_rule.py file.

Setup: As Admin, create a third user, Finance User (Role: Manager). Modify your Standard Approval rule and add both the Administrator and Finance User to the Approver Sequence. You now have 3 total approvers for any expense (Manager, Admin, Finance).

Scenario A: Percentage Rule (60% Required)
Configure Rule: Set Approval Percentage Threshold to 60 and make sure Hybrid Rule is unchecked.

Submit Expense as Test Employee.

First Approval: Log in as Test Manager and Approve. (1 of 3 approved = 33%). The expense should remain Submitted, and the current approver should change to the next in line.

Second Approval: Log in as Finance User and Approve. (2 of 3 approved = 66%).

Verification: ✅ As soon as the second approval happens, the expense status should automatically change to Approved because the 60% threshold has been met.

Scenario B: Specific Approver Rule (Admin is Key)
Configure Rule: Set the Specific Approver field to your Administrator user. Uncheck Hybrid Rule.

Submit Expense as Test Employee.

First Approval: Log in as Test Manager and Approve. The expense remains Submitted.

Second Approval: Log in as Administrator and Approve.

Verification: ✅ The moment the Administrator approves, the expense status should immediately change to Approved, regardless of the percentage.

## Phase 5: Testing Rejection
Submit a new expense as Test Employee.

Log in as Test Manager.

Find the expense in "Expenses to Approve" and click Reject.

Verification: ✅ The expense status should immediately change to Refused, and the approval process should stop completely.
