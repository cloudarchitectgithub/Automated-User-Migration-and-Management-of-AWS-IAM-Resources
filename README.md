# Automated User Migration and Management of AWS Identity and Access Management (IAM) Resources

<p align="center">
  <img src="https://i.imgur.com/MydpkxV.png" height="80%" width="80%" alt="Project Banner"/>
</p>

## Project Description
In this project, based on a real-world scenario, I took on the role of Cloud Specialist, responsible for automating the migration of 100 users to AWS and managing IAM (Identity and Access Management) resources. The goal was to ensure each user had multi-factor authentication (MFA) enabled on their accounts, following security best practices. The process began by setting up IAM groups, migrating users, and establishing appropriate access controls. The project culminated with enforcing MFA for both root and IAM users, and updating the password policy to meet security standards. To streamline the workflow and avoid repetitive manual tasks in the AWS console, I focused on automating key processes.

## Project Objective
The objective of this project was to automate the migration of 100 users to AWS Identity and Access Management (IAM) while ensuring the highest level of security through the implementation of Multi-Factor Authentication (MFA) and updated password policies. The key goals were to:

1. **Efficiently migrate users to AWS IAM, minimizing manual intervention and errors.**
2. **Organize users into appropriate IAM groups with well-defined access controls based on their roles and responsibilities.**
3. **Enforce MFA for all users, including both root and IAM accounts, as part of the security best practices.**
4. **Automate key steps of the migration process to reduce administrative overhead and ensure scalability for future user management.**
5. **Update the password policy to align with industry-standard security requirements, ensuring strong password usage and periodic updates for enhanced security.**
6. **Conduct thorough testing of the automated process to validate user creation, MFA enforcement, and password policy compliance.**

## Tools and Technologies
- **AWS IAM (Identity and Access Management)**
- **AWS CLI (Command Line Interface)**
- **Spreadsheet Software (e.g., Microsoft Excel, Google Sheets)**
- **Google Authenticator or other MFA applications**

---

## Project Solution
The solution for this project involved a structured approach to automate the migration of 100 users to AWS Identity and Access Management (IAM) and ensure compliance with AWS security best practices, including Multi-Factor Authentication (MFA) and password policy updates. The project was divided into several key phases:

### 1. Setting Up IAM Groups
To ensure proper access control, the first step was to create the necessary IAM groups for organizing users based on their roles and permissions. These groups included Admins, Developers, and a Trainees group for new users. This organization facilitated easier management of permissions and roles across the AWS environment.

### 2. Automating User Migration
A major focus of the project was the automation of user creation to minimize manual effort and avoid errors during the migration process. To achieve this, an AWS CLI-based automation script was developed and used. The process involved:
- **Preparing a Spreadsheet Input:** A spreadsheet template was created with fields like username, email address, and role. This file acted as the input for the script that would generate AWS IAM user accounts.
- **Converting the Spreadsheet:** The spreadsheet file was processed to remove any unnecessary fields and convert it into a format suitable for the AWS CLI script.
- **Running the AWS CLI Script:** The automation script took the prepared file and automatically created 100 IAM user accounts in AWS. This eliminated the need to manually create each user via the AWS Management Console.
- **Verifying User Creation:** After running the script, a series of tests were conducted to verify that all users were successfully created and assigned to the correct IAM groups. The AWS CLI was used to check each user’s permissions and group memberships.

### 3. Enforcing MFA
Once the users were created, the next phase involved enforcing Multi-Factor Authentication (MFA) for both IAM and root accounts. MFA was enabled as an additional security layer, and users were provided with instructions on how to configure MFA using their virtual or hardware devices. An automation script was also utilized to enforce MFA settings across all users, ensuring consistency.

### 4. Updating Password Policy
To strengthen security further, the AWS password policy was updated. The new policy enforced:
- A minimum password length of 12 characters.
- The requirement for uppercase letters, lowercase letters, numbers, and special characters.
- Password expiration every 90 days.
- A restriction on password reuse to ensure strong and regularly updated passwords.

### 5. Testing and Validation
The final phase of the project involved thorough testing to ensure the automation was successful and the security measures were properly enforced. This included:
- Verifying user creation and group assignments.
- Checking MFA enforcement for all users.
- Ensuring the password policy met the organization’s security standards.
- Conducting login tests for IAM users to validate access and MFA functionality.

The combination of automation and security controls not only streamlined the user migration process but also ensured adherence to security best practices, significantly reducing the risk of unauthorized access and enhancing overall cloud security.

---

## Step-by-Step Directions

### Step 1: Login to the AWS Management Console
1. Open your web browser and navigate to the [AWS Management Console](https://console.aws.amazon.com/).
2. Enter your AWS account credentials to log in.

<p align="center">
  <img src="https://i.imgur.com/mWaUUnT.png" height="80%" width="80%" alt="AWS Login Screenshot"/>
</p>

### Step 2: Create IAM Groups
1. In the AWS Management Console, navigate to the IAM service by clicking on "Services" in the top left corner, then selecting "IAM" under the Security, Identity, & Compliance category.
2. Click on "Groups" in the left-hand navigation pane.
3. Click the "Create New Group" button.

<p align="center">
  <img src="https://i.imgur.com/ZpJq9Xd.png" height="80%" width="80%" alt="Create IAM Group Screenshot"/>
</p>

4. Provide a name for the group (e.g., "CloudAdmin").

<p align="center">
  <img src="https://i.imgur.com/hJtEkpq.png" height="80%" width="80%" alt="Additional IAM Groups Screenshot"/>
</p>

5. Click "Next Step."
6. Attach policies to the group by searching for the relevant policy name (e.g., "AdministratorAccess" for the CloudAdmin group).

<p align="center">
  <img src="https://i.imgur.com/HUdCtLj.png" height="80%" width="80%" alt="User Data Spreadsheet Screenshot"/>
</p>   
7. Select the appropriate policy from the list and click "Next Step."
8. Review the group details and click "Create Group."

### Step 3: Create Additional IAM Groups
Repeat Step 2 to create additional IAM groups for different teams, such as "DBAs," "LinuxAdmin," "NetworkAdmin," and "Trainees." Associate the relevant policies based on the teams' responsibilities.

<p align="center">
  <img src="https://i.imgur.com/mOoyNLt.png" height="80%" width="80%" alt="Additional IAM Groups Screenshot"/>
</p>

### Step 4: User Creation Process Using Automation Script
1. **Review IAM Group Setup:** Ensure that all required IAM groups have been created. Create any missing groups if necessary.
2. **Prepare User Data Spreadsheet:** Gather the necessary information for the new users, such as usernames, full names, email addresses, and other relevant details. Organize this data in a spreadsheet format, which will be used as input for the user creation automation.

<p align="center">
  <img src="https://i.imgur.com/IKLKTOa.png" height="80%" width="80%" alt="User Data Spreadsheet Screenshot"/>
</p>

3. **Implement User Creation Automation Script:**
   - Install `dos2unix` on AWS CLI (required by the script).
  
<p align="center">
  <img src="https://i.imgur.com/Lcwf4Ha.png" height="80%" width="80%" alt="AWS CLI Script Screenshot"/>
</p>

   - Download the `aws-iam-create-user.sh` script on AWS Cloud Shell.

<p align="center">
  <img src="https://i.imgur.com/s27944Q.png" height="80%" width="80%" alt="AWS CLI Script Screenshot"/>
</p>
   - Give the proper permissions to the script.

   <p align="center">
  <img src="https://i.imgur.com/tDj8HQy.png" height="80%" width="80%" alt="AWS CLI Script Screenshot"/>
</p>

   - Upload the `users.csv` file to AWS Cloud Shell.

<p align="center">
  <img src="https://i.imgur.com/FAsHDNa.png" height="80%" width="80%" alt="AWS CLI Script Screenshot"/>
</p>

4. **Execute User Creation Script:** Run the automation script using the prepared user data spreadsheet. Verify that the IAM users are successfully created and associated with the appropriate IAM groups.

<p align="center">
  <img src="https://i.imgur.com/yrOYp75.png" height="80%" width="80%" alt="User Creation Script Execution Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/hJF0Yc3.png" height="80%" width="80%" alt="Password Policy Screenshot"/>
</p>

5. **Set Password Policies for All Groups:** For example, for the CloudAdmin group, set the `IAMUserChangePassword` policy.

<p align="center">
  <img src="https://i.imgur.com/cAIdv3z.png" height="80%" width="80%" alt="Password Policy Screenshot"/>
</p>

6. **Implement Multi-Factor Authentication (MFA) for Root User:** Enable MFA for the root user of the AWS account. This provides an additional layer of security for the AWS root account.

7. **Create a New IAM Group for Trainees:** Create a new IAM group specifically for trainees or users who require read-only access to AWS resources. Define a custom policy that provides only the necessary read permissions for this group.

<p align="center">
  <img src="https://i.imgur.com/rZPgIAW.png" height="80%" width="80%" alt="Trainees Group Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/8dNCSj4.png" height="80%" width="80%" alt="Trainees Group Screenshot"/>
</p>

8. **Associate Users with the Trainees Group:** Assign the relevant users, such as trainees or read-only users, to the newly created IAM group for trainees.

<p align="center">
  <img src="https://i.imgur.com/n8uvbCI.png" height="80%" width="80%" alt="Associate Users Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/pz3OXwF.png" height="80%" width="80%" alt="Associate Users Screenshot"/>
</p>

9. **Implement IAM Password Policy:** Configure an IAM password policy to enforce strong password requirements for all IAM users. This includes setting minimum password length, requiring alphanumeric characters, etc. Add the `IAMUserChangePassword` policy to all groups (e.g., Trainees group: `ChangeMe123456!`).

<p align="center">
  <img src="https://i.imgur.com/2XBaO3r.png" height="80%" width="80%" alt="IAM Password Policy Screenshot"/>
</p>

10. **Test MFA Enforcement:**
    - Select a user to test (e.g., `angelino.marinho`).
    - Reset the password.
   
    <p align="center">
  <img src="https://i.imgur.com/GqWKTSM.png" height="80%" width="80%" alt="MFA Enforcement Screenshot"/>
</p>

-	Attempt to Access AWS Services Without MFA:
-	Log in as the selected user.
-	Try to perform an action (e.g., create a database).
-	Verify that access is denied due to missing MFA.

<p align="center">
  <img src="https://i.imgur.com/CtcKe1x.png" height="80%" width="80%" alt="MFA Enforcement Screenshot"/>
</p>

-	Enable MFA for the Test User:
-	Go to the user’s details and click "My Security Credentials."

<p align="center">
  <img src="https://i.imgur.com/PaJab3B.png" height="80%" width="80%" alt="Enforce MFA Policy Screenshot"/>
</p>

### Step 5: Enable Multi-Factor Authentication (MFA) on Root User
1. Enable MFA for the root user account.

<p align="center">
  <img src="https://i.imgur.com/H1UXtu3.png" height="80%" width="80%" alt="MFA for Root User Screenshot"/>
</p>

2. Download an authenticator app on your smartphone (e.g., Google Authenticator).
3. Configure the authenticator app with the AWS account using the QR code provided in the AWS console.

<p align="center">
  <img src="https://i.imgur.com/3UO7Vyr.png" height="80%" width="80%" alt="MFA for Root User Screenshot"/>
</p>
   
4. Assign the MFA device to the root user.

<p align="center">
  <img src="" height="80%" width="80%" alt="MFA for Root User Screenshot"/>
</p>

### Step 6: Create and Attach Enforce MFA Policy
1. Download the provided JSON file containing the policy to enforce multi-factor authentication.
2. Create a new policy in the AWS IAM service using the JSON file.
3. Attach the enforce MFA policy to the IAM groups associated with the IAM users.

<p align="center">
  <img src="https://i.imgur.com/eoTmLTR.png" height="80%" width="80%" alt="Enforce MFA Policy Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/w7EpSSs.png" height="80%" width="80%" alt="Enforce MFA Policy Screenshot"/>
</p>

4. Attach the enforce MFA policy to all the IAM groups ex; CloudAdmin Group associated with the IAM users.

<p align="center">
  <img src="https://i.imgur.com/P8M7wU0.png" height="80%" width="80%" alt="Password Policy Update Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/658wCjw.png" height="80%" width="80%" alt="Password Policy Update Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/hn4odeK.png" height="80%" width="80%" alt="Password Policy Update Screenshot"/>
</p>

### Step 7: Update AWS Password Policy
1. In the IAM Dashboard, go to Account Settings.
2. Under Password Policy, review the current settings.
3. To enhance security, enable the following:
   - Password must contain at least one uppercase letter.
   - Password must contain at least one lowercase letter.
   - Password must contain at least one number.
   - Optionally, add other requirements like special characters or length.
   
   <p align="center">
  <img src="https://i.imgur.com/WUgl4IC.png" height="80%" width="80%" alt="Password Policy Update Screenshot"/>
</p>

4. Click "Save Changes" to update the password policy.

### Step 8: Test User Access Before and After MFA Enablement
1. Log in as a test user (e.g., Jane Doe) and attempt to access AWS resources without MFA. Verify that access is denied.
2. Enable MFA for the test user and log in again. Verify that access is granted after MFA is enabled.

<p align="center">
  <img src="https://i.imgur.com/odyPNo8.png" height="80%" width="80%" alt="MFA Test Screenshot"/>
</p>

### Step 9: Enable MFA for a Test User
-	Go back to the IAM Console.
-	Select the user account you want to enable MFA for, for example, Jane Doe.
-	Click on Security Credentials and navigate to the Multi-factor authentication (MFA) section.

<p align="center">
  <img src="https://i.imgur.com/BEZ9wJ0.png" height="80%" width="80%" alt="MFA Troubleshooting Screenshot"/>
</p>

-	Click Assign MFA device and choose Virtual MFA Device.
-	Use an authentication app like Google Authenticator or Authy to scan the QR code displayed.

<p align="center">
  <img src="https://i.imgur.com/Vb8xRfz.png" height="80%" width="80%" alt="MFA Troubleshooting Screenshot"/>
</p>

-	Enter the two consecutive codes generated by the app.
-	Click Assign MFA to enable MFA for the user.

### Step 10: Test User Access After MFA Enablement
-	Log out of the AWS Console and log back in as the test user (Jane Doe or another).
-	Now, upon logging in, you should be prompted for the MFA code from the authentication app.

<p align="center">
  <img src="https://i.imgur.com/Chz2ECK.png" height="80%" width="80%" alt="MFA Troubleshooting Screenshot"/>
</p>

-	After successful MFA login, try the same actions, such as:
o	Search for RDS again.
o	Attempt to create a database.
-	The user should now be able to create the database or perform other permitted actions because MFA is enabled.

<p align="center">
  <img src="https://i.imgur.com/9VgQeXJ.png" height="80%" width="80%" alt="MFA Troubleshooting Screenshot"/>
</p>

### Step 10: Troubleshoot Potential MFA Issues
-	If you encounter issues like MFA device conflicts (e.g., an error asking for the removal of a device), you can either:
-	Use the AWS CLI to remove the existing MFA device.
-	Refer to the AWS documentation for resolving MFA conflicts.
-	As an alternative, you can log in as an administrator and reassign the MFA device to resolve the issue.


---

## Project Conclusion
The project successfully migrated users to AWS IAM, configured MFA for enhanced security, and enforced MFA policies across all relevant IAM groups. The implementation of these security measures ensures that only users with MFA enabled can access and perform actions within the AWS environment. This approach mitigates the risk of unauthorized access and potential data breaches, aligning with best practices for cloud security management.
