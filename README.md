Customer Onboarding Automation (Power Automate)
📌 Overview

This solution automates the handoff of new customers from Microsoft Forms → SharePoint → Microsoft Teams/Planner.
When a new form response is submitted, it is written into the SharePoint list (OnboardingTable). The flow then creates a Planner task in the appropriate bucket and optionally sends a notification to Teams/Outlook.

⚙️ Workflow Summary

Trigger:

When a new response is submitted (Microsoft Forms) → Create item in SharePoint (OnboardingTable)

When an item is created in SharePoint (OnboardingTable)

Logic (Switch):
Uses the OnboardingStatus field to route tasks to the right Planner bucket:

🟢 New Signup → Planner bucket "New Signup"

🟡 In Progress → Planner bucket "In Progress"

🔴 Escalations → Planner bucket "Escalations"

✅ Completed → Planner bucket "Completed"

Actions (per case):

Create a task in Automation Demo → Onboarding Plan

Title: "New customer: " + Customer

Assigns task to the correct Bucket Id

Optional Notifications (general step):

Teams post or Outlook email:
"New onboarding task created for [Customer] in [Bucket]."

📂 Structure

The solution includes:

Cloud Flow: Customer Handoff – New Signup

Connections:

Microsoft Forms (Customer Signup)

SharePoint (OnboardingTable)

Planner

Microsoft Teams (optional for notifications)

🚀 Setup Instructions
Microsoft Forms

Create a form called Customer Onboarding Signup with fields:

Customer (Text)

SignupDate (Date)

OnboardingStatus (Choice: New Signup, In Progress, Escalations, Completed)

TimeToValueDays (Text with Number restriction)

Revenue (Text with Number restriction)

Churned (Choice: Yes/No)

Connect this form to Power Automate:

Trigger: When a new response is submitted (Microsoft Forms)

Action: Get response details

Action: Create item in SharePoint → OnboardingTable

This ensures onboarding always starts with a simple form entry (internal or external), and feeds directly into the automation.

SharePoint

Create a list called OnboardingTable with columns:

Title (used as Customer name)

OnboardingStatus (choice: New Signup, In Progress, Escalations, Completed)

TimeToValueDays (number)

Revenue (number)

Churned (Yes/No)

SignupDate (date)

Planner (inside Teams)

Team: Automation Demo

Plan: Onboarding Plan

Buckets: 🟢 New Signup, 🟡 In Progress, 🔴 Escalations, ✅ Completed

Power Automate Flow

Trigger: When item is created → SharePoint OnboardingTable

Switch: OnboardingStatus

Cases: New Signup / In Progress / Escalations / Completed

Action: Create a task → map bucket accordingly

(Optional): Add Teams/Outlook step after Create a task

📸 Example Flow

Flow overview:
(Insert your own screenshot of the flow canvas here)

🔒 Limitations

Export to .zip (managed/unmanaged) is disabled in this environment.

Instead, this repo documents the flow structure with screenshots and instructions.

To recreate, import manually into Power Automate using the steps above.

👩‍💻 Author

Publisher: Steward Development (Internal)

Flow Owner: Debora Pichel Rois

📜 License

MIT License – feel free to reuse with attribution.
