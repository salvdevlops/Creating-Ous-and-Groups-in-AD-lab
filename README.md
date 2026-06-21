# Creating OUs and Groups in Active Directory

## Description: In this lab, we will structure our Active Directory environment by creating Organizational Units (OUs), categorizing departments, and provisioning domain admin and regular user accounts.

## Tools Used

* **[Active Directory Users and Computers (ADUC)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-g--securing-administrators-groups-in-active-directory)** - The primary Microsoft Management Console (MMC) snap-in used to administer Active Directory objects and their attributes.
* **[Server Manager](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/server-manager)** - The management console used to provision and manage Windows Server roles and features.

## Environments Used

* **[Windows Server 2025](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2025)** - The server operating system functioning as our Domain Controller.

## Step 1: Open Active Directory Users and Computers

First, open **Active Directory Users and Computers** from the Server Manager tools.

<img width="340" height="84" alt="image" src="https://github.com/user-attachments/assets/843b0675-c241-4a1d-85ef-c090b43a75fd" />

---

## Step 2: Create the Top-Level OU

1. Expand your domain in the left-hand pane.
2. Right-click on the domain, scroll down to **New**, and select **Organizational Unit**.
3. Type `USA` for the name and click OK.

<img width="748" height="514" alt="image" src="https://github.com/user-attachments/assets/62a99b35-701f-4f81-a9fd-86d5363b49f2" />

---

## Step 3: Create Sub-OUs for Users and Computers

Next, we will create sub-OUs under `USA` for `Users` and `Computers`. Since companies have different types of users based on their departments, this is how we categorize and structure the directory. 

Right-click the `USA` OU, select **New** > **Organizational Unit**, and create two separate OUs. It should look like the image below:

<img width="744" height="523" alt="image" src="https://github.com/user-attachments/assets/fd6eb28e-feba-4e00-b506-2d4bdffcd0c0" />

---

## Step 4: Create Departmental Sub-OUs

Next, we will create three department OUs under the new `Users` OU:

1. Right-click on `Users`, go to **New**, and select **Organizational Unit**.
2. Type `IT` and click OK.
3. Repeat this process twice more to create an `HR` OU and a `Finance` OU. 

Once finished, your structure should look like this:

<img width="756" height="378" alt="image" src="https://github.com/user-attachments/assets/9cb449c6-fb3d-4d49-aded-24d22d6219b1" />

---

## Step 5: Create a Domain Admin Account

Now that we have our departmental OUs, we need to create user accounts. We'll start with a Domain Admin. 

1. Right-click on the **IT** OU (since IT staff usually require domain admin rights).
2. Click **New** > **User**.
3. Fill in the user details of your choice and click Next.

<img width="739" height="484" alt="image" src="https://github.com/user-attachments/assets/ce33f4f9-8c1c-430f-8496-03093e09057d" />

4. Choose a strong password and save it securely. 
5. Ensure that **only** the `Password never expires` box is checked, then click Next and Finish.

<img width="722" height="501" alt="image" src="https://github.com/user-attachments/assets/11832772-f035-4557-aa1e-b3616c6c6453" />

---

## Step 6: Assign Domain Admin Rights

We need to add our newly created IT user to the Domain Admins group.

1. Double-click the user you just created to open their Properties.
2. Navigate to the **Member Of** tab.
3. Click **Add**.
4. Type `Domain Admins` in the object names box.
5. Click **Check Names** (it should underline to confirm it resolved correctly), then click **OK**.

Your new user is now a Domain Admin. The properties window should look like this:

<img width="892" height="586" alt="image" src="https://github.com/user-attachments/assets/b28e1130-397c-499d-88c7-fbe6a750c4e0" />

---

## Step 7: Create a Regular User Account

Finally, we will create a standard user account.

1. Right-click on the **HR** OU, select **New**, and click **User**.
2. Choose a name and fill out the details.
3. Set a password, leaving only the `Password never expires` box checked.
4. Click **Finish**. 

You should now see the standard user residing under the HR OU:

<img width="581" height="369" alt="image" src="https://github.com/user-attachments/assets/0a562ce7-1b64-4487-bd14-9bfcbedeb339" />

Next Lab: https://github.com/salvdevlops/Joining-a-Windows-11-client-to-Active-Directory-Domain-lab/edit/main/README.md

