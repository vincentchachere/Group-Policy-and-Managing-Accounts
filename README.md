=<br>

<p align="center">
<img width="700" src="https://github.com/user-attachments/assets/9b6b0a51-6411-4e01-96c5-1bb31e6fd986" alt="Microsoft Active Directory Logo"/>
<br>

<br>

<br>

<h1 align="center">Group Policy and Account Managing</h1> 
<br>

<p align="center">
<img src="https://github.com/user-attachments/assets/8cfd35a9-966b-4922-bed7-8555bf9853cc" height="85%" width="85%" alt="9"/><br />
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

- 
- 
- 
- 
- 

## Configuration Steps

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/2997cf73-1121-4273-83dc-f248e9468781">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/67d9d84d-b83f-423e-a6bf-8f8cc099d95a">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/491a7a4d-12cc-4fb3-b52f-d1f018ed027c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/dec2211c-aba6-4361-9bdb-079523de8dc5">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/f4f96834-19db-4c97-84de-625a4b9b5a7b">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/048278cd-4361-4d99-bfe7-8f2ae1915eeb">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/7203ae6d-354c-4353-9228-211131cbd87c">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/80c28508-e99d-4435-95d4-1591387bf2bb">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/679a2fe7-097d-4509-9c9b-f357f76c3233">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e6512855-2c3a-4ffa-b3d5-8052e054aa56">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e87fd670-2cab-45fb-8f86-bd245c67a20f">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/3208e8ab-6e60-4710-860c-f16a478aba46">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/347c8c3b-c485-4337-b1bd-f9d78971236a">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/e74559fb-52f9-4988-a69b-937c00529158">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ade102b9-562b-4eed-9c39-a34a55f28761">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/45dcd2b2-9263-4c1d-8618-3516cc1e36e9">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/d9b18e31-984d-4a8e-94b4-d45cd8293116">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/ededc232-8ed3-4cf3-ad8f-901e5718848f">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/b5f8615a-8dba-41d0-9193-db8acc203cc8">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/517e88e3-6647-446b-a924-320eadb6dcd2">

<br>
<br>
<br>

<img width="800" alt="isolated" src="https://github.com/user-attachments/assets/a685ac6d-aaed-462f-88d0-02f4209f13e8">

<br>
<br>
<br>

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

