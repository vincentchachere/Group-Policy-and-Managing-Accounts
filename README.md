<br>

<p align="center">
<img width="700" src="https://github.com/user-attachments/assets/9b6b0a51-6411-4e01-96c5-1bb31e6fd986" alt="Microsoft Active Directory Logo"/>
<br>

<br>

<br>

<h1 align="center">Group Policy and Account Management</h1> 
<br>

<p align="center">
<img src="https://github.com/user-attachments/assets/8cfd35a9-966b-4922-bed7-8555bf9853cc" height="60%" width="60%" alt="9"/><br />
</p>
<br />

## Lab Overview

This lab builds on the previous one [here](https://github.com/vincentchachere/Active-Directory-Deployment-and-Configuration/edit/main/README.md). This lab focuses on learning key Active Directory skills like managing account lockouts, password resets, enabling/disabling accounts, and analyzing event logs. You’ll also configure Group Policy to enforce security settings, such as account lockout thresholds, and test these configurations in a realistic environment.

## Environments and Technologies Used

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- Group Policy Management Console (GPMC)
- Event Viewer
- PowerShell

## Operating Systems Used

- Windows Server 2022
- Windows 10 (21H2)

## High-Level Group Policy and Account Managing Steps

- Group Policy Configuration
- Account Lockout
- Account Recovery
- Password Reset
- Enable/Disable Accounts
- Log Observation

## Configuration Steps

<details>

<summary>

### 🔒 Part 1: Group Policy Configuration

</summary>

*First, we will configure a group policy to practice account lockoout.*

- Log into DC-1: as `mydomain.com\jane_admin`

- Search and Go To: `gpmc.msc` (Group Policy Management Console - Microsoft)

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/67d9d84d-b83f-423e-a6bf-8f8cc099d95a">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

- Expand: `Forest: mydomain.com` > `Domains` > `mydomain.com`

- Right-Click: `Default Domain Policy`

- Select: `Edit`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/491a7a4d-12cc-4fb3-b52f-d1f018ed027c">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

Now, you are inside **Group Policy Management Editor** where you can edit group policies.

- Expand: `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Account Policies`

- Select: `Account Lockout Policy`

- Select: `Account lockout duration`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/078b88cd-f967-4346-9175-8d9788b11fdf">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*Within Account lockout **duration** Properties*

- Check: the `Define this policy setting` box

- Account is locked out for: `30 minutes`

- Select: `Apply`

*It will end you to the **Suggested Value Changes** window after this.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f4f96834-19db-4c97-84de-625a4b9b5a7b">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*When the **Suggested Value Changes** window pops up*

- Click: `OK`

- Click: `OK` again when back inside Account lockout duration Properties then..

- Open: `Account lockout threshold`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/048278cd-4361-4d99-bfe7-8f2ae1915eeb">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*Within Account lockout **threshold** Properties*

- Check: the `Define this policy setting` box

- Account will lock out after: `5 invalid logon attempts`

- Select: `Apply`

*It will end you to the **Suggested Value Changes** window after this.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7203ae6d-354c-4353-9228-211131cbd87c">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*When the **Suggested Value Changes** window pops up*

- Click: `OK`

- Click: `OK` again when back inside Account lockout threshold Properties

*Next, we will check the **Default Domain Policy**, which will be inside Group Policy Management (not Group Policy Management Editor) to verify that the configured Group Policy settings have been applied.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/80c28508-e99d-4435-95d4-1591387bf2bb">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*Back inside Group Policy Management*

- Expand: `Forest: mydomain.com` > `Domains` > `mydomain.com`

- Select: `Default Domain Policy`

- Click: `Close`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/679a2fe7-097d-4509-9c9b-f357f76c3233">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*Within Default Domain Policy*

- Select: the `Settings` tab

- Scroll down to: `Computer Configuration (Enabled)`

*In the Account Policies/Account Lockout policy section you will see the Group Policy settings that you've just configured have been applied.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e6512855-2c3a-4ffa-b3d5-8052e054aa56">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*Now we will force apply the group policy inside command prompt as an administrator to immediately apply it, avoiding the 90-minute default propagation delay for all user accounts.*

- Log back into Client-1 as: `mydomain.com\jane_admin`

- Run: `Command Prompt as an Administrator`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/97cb95cd-4102-4cd7-9481-1acebe72c4c4">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

- Run the Command: `gpupdate /force` to force apply the group policy

*As you'll see the group policy has been successfully forced aplied.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/21352492-32cc-441d-ae08-8432bfe7780f">

<br>
<br>
<br>

<ins>Configuring a Group Policy<ins>:

*If you run the command **gpresult /r** you will be able to see the last time the group policy was applied.**

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/50d10077-1819-4d93-8797-5e6003947306">

</details>

<details>

<summary>

### 🔒 Part 2: Account Lockout

</summary>

*Now that the Group Policy is created we can attempt 6+ failed logins on Client-1 with a created user account to verify lockout in ADUC.*

- Disconnect: from `Client-1 from Remote Desktop (RDP)` if you haven't already

- Pick a random user account you previously created, [in this lab](https://github.com/vincentchachere/Active-Directory-Deployment-and-Configuration), and attempt 6+ failed logons.

*Later, we will review these actions in the Event Logs for verification and analysis.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ade102b9-562b-4eed-9c39-a34a55f28761">

<br>
<br>
<br>

<ins>Account Lockout<ins>:

*This message will pop up when your users account has been successfully locked out.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/45dcd2b2-9263-4c1d-8618-3516cc1e36e9">

</details>

<details>

<summary>

### 🔒 Part 3: Account Recovery

</summary>

<ins>Account Recovery<ins>:

*Go back into DC-1 (as mydomain.com\jane_admin) and go to ADUC.*

- Right-Click: `mydomain.com`

- Select: `Find`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d9b18e31-984d-4a8e-94b4-d45cd8293116">

<br>
<br>
<br>

<ins>Account Recovery<ins>:

- Search: `User Account` (Example: bav.vow)

- Double-Click: `User Account` (Example: bav.vow)

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ededc232-8ed3-4cf3-ad8f-901e5718848f">

<br>
<br>
<br>

<ins>Account Recovery<ins>:

*Inside User Account Properties*

- Go To: `Account`

- Check: the `Unlock account. This account is currently locked out on this Active Directory Domain Controller.` box

- Select: `Apply`

- Click: `OK`

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b5f8615a-8dba-41d0-9193-db8acc203cc8">

<br>
<br>
<br>

<ins>Account Recovery<ins>:

*Now you will be able to successfully log into Client-1 with your created user account.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/517e88e3-6647-446b-a924-320eadb6dcd2">

<br>
<br>
<br>

<ins>Account Recovery<ins>:

*Once inside Client-1 as your created user account you can open powershell and run the command **whoami** to notice that you're logged in as your created user account.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a685ac6d-aaed-462f-88d0-02f4209f13e8">

</details>

<details>

<summary>

### 🔒 Part 4: Password Reset

</summary>

Next we'll practice reseting the password for your created user account.*

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/77702170-e664-4e1c-a9ed-edbf3b8490dd">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/1e37e51e-40ff-4cd0-a048-688e900db166">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c0f1ec00-21a8-4d15-987f-d50f039b7ae0">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/affd1223-979b-48b4-b092-0e7b6411df29">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/5cc6a87c-9ed2-4e56-8995-c5a8d40622a2">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/651a4194-9edc-4e09-b944-c427931a3e93">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/c93d593e-8b15-4dec-93a2-50318b9fffbc">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e1b18b01-93f8-4cb4-bad4-57220a50254d">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/fc71e9e5-6358-4794-85b8-3a5940054c87">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/2d6a8e88-f74a-403d-9c7d-ef531efa7e46">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/2d48f55e-1090-4a71-8e03-58f6efefd35b">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3f9d26d9-a31f-4388-ba80-425310bf1a96">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ee51e554-914a-4ddb-b218-c86fdf6e3259">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/afaadee4-ca16-4fe1-8c7f-3c19f89ee568">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/4e7810c3-8169-42f8-9bcd-3ef40b6f2cfe">

<h2 align="center">Final Thoughts</h2>



☎️ For any questions or just to connect you can reach me at: www.linkedin.com/in/vincentchachere
