# Notification Templates

## Microsoft Teams (Post message in a chat or channel)

New Onboarding Task
• Customer: @{triggerOutputs()?['body/Title']}
• Status: @{triggerOutputs()?['body/OnboardingStatus']}
• Revenue: $@{triggerOutputs()?['body/Revenue']}
• TTV (days): @{triggerOutputs()?['body/TimetoValueDays']}


## Outlook (Send an email (V2))
- **Subject:** New onboarding task – @{triggerOutputs()?['body/Title']}  
- **Body (HTML):**

p><strong>New Onboarding Task</strong></p> <ul> <li><strong>Customer:</strong> @{triggerOutputs()?['body/Title']}</li> <li><strong>Status:</strong> @{triggerOutputs()?['body/OnboardingStatus']}</li> <li><strong>Revenue:</strong> $@{triggerOutputs()?['body/Revenue']}</li> <li><strong>TTV (days):</strong> @{triggerOutputs()?['body/TimetoValueDays']}</li> </ul> ``` ```
