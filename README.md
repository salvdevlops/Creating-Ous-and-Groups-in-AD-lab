# Creating OUs and Groups in Active Directory

## Overview
This lab structures an Active Directory environment from the ground up: building out Organizational Units (OUs), categorizing departments, and provisioning both a domain admin account and a regular user account.

## Tools Used
- **[Active Directory Users and Computers (ADUC)](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-g--securing-administrators-groups-in-active-directory)** — the primary MMC snap-in used to administer AD objects and their attributes.
- **[Server Manager](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/server-manager)** — the management console used to provision and manage Windows Server roles and features.

## Environment
- **[Windows Server 2025](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2025)** — the server OS functioning as the Domain Controller.

---

## Step 1: Open Active Directory Users and Computers

Open **Active Directory Users and Computers** from the Server Manager tools.

<img width="340" height="84" alt="image" src="https://github.com/user-attachments/assets/843b0675-c241-4a1d-85ef-c090b43a75fd" />

## Step 2: Create the Top-Level OU

1. Expand the domain in the left-hand pane.
2. Right-click the domain → **New** → **Organizational Unit**.
3. Name it `USA` and click **OK**.

<img width="748" height="514" alt="image" src="https://github.com/user-attachments/assets/62a99b35-701f-4f81-a9fd-86d5363b49f2" />

## Step 3: Create Sub-OUs for Users and Computers

Next, create sub-OUs under `USA` for `Users` and `Computers`. Since companies have different types of users across departments, this is how the directory gets categorized and structured.

Right-click the `USA` OU → **New** → **Organizational Unit**, and repeat for both sub-OUs. It should look like the image below:

<img width="744" height="523" alt="image" src="https://github.com/user-attachments/assets/fd6eb28e-feba-4e00-b506-2d4bdffcd0c0" />

## Step 4: Create Departmental Sub-OUs

Create three department OUs under the new `Users` OU:

1. Right-click `Users` → **New** → **Organizational Unit**.
2. Name it `IT` and click **OK**.
3. Repeat to create `HR` and `Finance` OUs.

Once finished, the structure should look like this:

<img width="756" height="378" alt="image" src="https://github.com/user-attachments/assets/9cb449c6-fb3d-4d49-aded-24d22d6219b1" />

## Step 5: Create a Domain Admin Account

With the departmental OUs in place, the next step is creating user accounts — starting with a Domain Admin.

1. Right-click the **IT** OU (IT staff typically require domain admin rights).
2. **New** → **User**.
3. Fill in the user details and click **Next**.

<img width="739" height="484" alt="image" src="https://github.com/user-attachments/assets/ce33f4f9-8c1c-430f-8496-03093e09057d" />

4. Choose a strong password and save it securely.
5. Ensure **only** the `Password never expires` box is checked, then click **Next** and **Finish**.

<img width="722" height="501" alt="image" src="https://github.com/user-attachments/assets/11832772-f035-4557-aa1e-b3616c6c6453" />

## Step 6: Assign Domain Admin Rights

Add the newly created IT user to the **Domain Admins** group.

1. Double-click the user to open their Properties.
2. Go to the **Member Of** tab.
3. Click **Add**.
4. Type `Domain Admins` in the object names box.
5. Click **Check Names** (it should underline to confirm it resolved), then click **OK**.

The user is now a Domain Admin. The properties window should look like this:

<img width="892" height="586" alt="image" src="https://github.com/user-attachments/assets/b28e1130-397c-499d-88c7-fbe6a750c4e0" />

## Step 7: Create a Regular User Account

Finally, create a standard user account.

1. Right-click the **HR** OU → **New** → **User**.
2. Fill in the name and details.
3. Set a password, leaving only `Password never expires` checked.
4. Click **Finish**.

The standard user should now appear under the HR OU.

---

## Key Takeaways
- OU structure should mirror how a company is actually organized (by department, by location, etc.) — not just dumped into the default containers.
- Domain Admin rights should be scoped narrowly and assigned deliberately, not handed out by default.
- `Password never expires` is a lab/home-lab convenience setting — in a production environment, this would be governed by a real password policy instead.
- This OU/account structure is the foundation the rest of the AD lab series builds on (security groups, permissions, and domain-joined clients all rely on it).
