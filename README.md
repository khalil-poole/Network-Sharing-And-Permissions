# Network-Sharing-And-Permissions

In this final part of the Active Directory Lab, we are going to create file and network sharing and permissions with different users and groups within the domain.

Let's start by logging back in with our two virtual machines. For the domain controller, we are still using jane_admin. For the client vm, you can use the user we created in previous sections.

Inside the domain controller vm, go to This PC, then double click Windows (C:), and from there, create 4 folders within the C:\ drive: “read-access”, “write-access”, “no-access”, “accounting” without the quotations.

<img width="961" height="594" alt="image" src="https://github.com/user-attachments/assets/210ecb6f-d61f-4ad9-9bc4-e40bdc46433b" />




Next, we are going to set the following permissions (share the folder)

Folder: “read-access”, Group: “Domain Users”, Permission: “Read”

Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”

Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”

Skip the Accounting folder for time being

To do this, right click on one of the folders and then click properties. Then we'll go to the "Sharing" tab, and then click on "Share".

<img width="998" height="737" alt="image" src="https://github.com/user-attachments/assets/7cdadada-c81c-4bf1-8685-a96a7ce9db28" />


<img width="476" height="592" alt="image" src="https://github.com/user-attachments/assets/590d7284-ea5e-43eb-87c6-c6664892280c" />


Inside the white text area we are going to type "domain users" exactly like that with no extra spaces after, and then click "Add" and then click "Share."


<img width="659" height="564" alt="image" src="https://github.com/user-attachments/assets/6f65114b-25a1-4bdd-a609-cf28800f19df" />


