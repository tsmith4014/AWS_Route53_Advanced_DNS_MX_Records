# Configuring AWS Route 53 for Google Workspace Gmail - MX Records

This guide provides step-by-step instructions on how to configure your domain's DNS settings in AWS Route 53 to use Google Workspace Gmail for email services. This setup enables you to receive emails at your custom domain through Google's email servers.

## Prerequisites

- An active domain registered in AWS Route 53.
- A Google Workspace account with your domain added and verified.
- Access to the AWS Management Console with permissions to edit Route 53 settings.

## Steps Overview

1. [Log into AWS Management Console](#step-1-log-into-aws-management-console)
2. [Access Route 53 Hosted Zone](#step-2-access-route-53-hosted-zone)
3. [Add MX Records for Google Workspace Gmail](#step-3-add-mx-records-for-google-workspace-gmail)
4. [Verify MX Records](#step-4-verify-mx-records)
5. [Testing Email Reception](#step-5-testing-email-reception)

### Step 1: Log into AWS Management Console

- Navigate to the [AWS Management Console](https://aws.amazon.com/console/).
- Sign in with your AWS account credentials.

### Step 2: Access Route 53 Hosted Zone

- In the AWS Management Console, go to **Services** and select **Route 53**.
- Click on **Hosted zones** in the Route 53 dashboard.
- Select the domain you want to configure for Google Workspace Gmail.

### Step 3: Add MX Records for Google Workspace Gmail

1. **Create New Record**:

   - Click on **Create record** or **Create record set**.
   - Choose the **Simple routing** policy and click **Next**.

2. **Define Simple Record**:

   - **Record name**: Leave blank or use `@` for the root domain.
   - **Record type**: Select **MX - Mail exchange**.
   - **Value/Route traffic to**: Enter the MX records as provided by Google Workspace, one per line, in the following format:
     ```
     1 ASPMX.L.GOOGLE.COM.
     5 ALT1.ASPMX.L.GOOGLE.COM.
     5 ALT2.ASPMX.L.GOOGLE.COM.
     10 ALT3.ASPMX.L.GOOGLE.COM.
     10 ALT4.ASPMX.L.GOOGLE.COM.
     ```
     Ensure each server address ends with a dot (`.`).
   - **TTL (seconds)**: Recommend `300` for quicker DNS updates during initial setup.

3. **Add to List**:

   - After entering the MX record details, add them to the list of records to create by clicking on **Define simple record**.

4. **Create Records**:
   - Review the MX records in the list for any errors.
   - Click **Create records** to finalize and add these MX records to your domain’s DNS settings.

### Step 4: Verify MX Records

- After adding the MX records, use a tool like [MXToolBox](https://mxtoolbox.com/MXLookup.aspx) to verify they're correctly pointing to Google's servers.
- Enter your domain and run the MX Lookup. The results should reflect the MX records you've just added.

### Step 5: Testing Email Reception

- Send a test email from a different email service to your domain's email address managed by Google Workspace Gmail.
- Check the inbox (and spam folder) for the test email to confirm successful receipt.

## Conclusion

By following these steps, you've successfully configured AWS Route 53 to route email traffic for your domain through Google Workspace Gmail. This setup enables you to leverage Google's robust email services for your custom domain.

---
