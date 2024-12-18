**Email Forward Digest Solution**

- This repository contains an Azure Logic App-based solution to address the challenges faced by customers in receiving forwarded military emails due to policy changes in military email addresses. 
- The solution generates a daily digest of email forwards and sends it to designated recipients. 
- It is designed to function without direct access to mail flow or mail gateways, making it a robust alternative for restricted environments.

**Overview**

The solution:
- Fetches email pairs from a SharePoint site.
- Retrieves emails for the specified accounts.
- Processes and aggregates the email data into a digest.
- Sends the digest via email to the appropriate recipients.
- This project was developed by me without prior experience in Power Automate or Logic Apps.

**Features**

- Daily Email Digest: Aggregates emails received within the past 24 hours and sends a summary.
- HTML Table Generation: Formats the email details (subject, sender, and receive time) into an easy-to-read HTML table.
- Dynamic Recipient Handling: Allows email recipient addresses to be dynamically specified.
- Secure Token Management: Utilizes Azure Key Vault to securely manage client IDs and secrets for Microsoft Graph API access.


**Prerequisites**

- An active Azure subscription.
- Access to Microsoft Graph API.
- A SharePoint site to store email pair configurations.
- Azure Key Vault for secure storage of credentials.

**Setup Instructions**

**1. Deploy the Logic App**

- Open the Azure Portal and create a new Logic App resource.
- Import the provided JSON definition into the Logic App.
- Save the Logic App.

**2. Configure Connections**

- Set up connections for the following:
- Microsoft Graph API
- SharePoint API
- Azure Key Vault
- Update the parameters section in the Logic App definition with the appropriate connection IDs.

**3. Populate SharePoint Site**

- Create a table in the SharePoint site to store email pairs.
- Ensure the table has the following columns:
- First Email: The email address to fetch emails from.
- Second Email: The email address to send the digest to.

**4. Secure Credentials**

- Store the following in Azure Key Vault:
- Client ID
- Client Secret
- Ensure the Logic App has access to the Key Vault.

**5. Test the Logic App**

- Trigger the Logic App manually to ensure proper configuration.
- Verify that emails are retrieved, processed, and sent as a digest.

**Usage**

- The Logic App runs on a daily schedule, fetching emails received in the past 24 hours.
- It generates an HTML table summarizing the emails.
- If emails are found, they are sent as a digest to the designated recipient.
- If no emails are found, a notification email is sent to inform the recipient.

**Key Components**

Triggers:

- Recurrence trigger for daily execution.

Actions:

- Fetch email pairs from SharePoint.
- Retrieve emails using Microsoft Graph API.
- Parse and format email data.
- Send email digest.

Dynamic Variables:

- Handles multiple email pairs in a loop.

Error Handling:

- Provides notifications in case of missing data.

Limitations

- Requires valid access tokens to interact with Microsoft Graph API.
- Dependent on SharePoint for email pair configurations.
- Designed for daily execution; modifications are needed for different frequencies.

Future Enhancements

- Add logging for better troubleshooting and monitoring.
- Extend compatibility for other email providers.
- Implement more robust error-handling mechanisms.
- Support multi-timezone configurations for recipients.
