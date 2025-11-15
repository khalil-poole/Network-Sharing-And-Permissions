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


Afterwards, go inside the white text area we are going to type "domain users" exactly like that with no extra spaces after, and then click "Add" and then click "Share." Then click done, then close.


<img width="659" height="564" alt="image" src="https://github.com/user-attachments/assets/6f65114b-25a1-4bdd-a609-cf28800f19df" />


<img width="658" height="554" alt="image" src="https://github.com/user-attachments/assets/87057bda-9548-45f9-b021-56a40e63683a" />


Repeat the next steps for the write-access folder, except once inside the Network access window, click on the down arrow under the "Permission Level" and change it from Read to Read/Write.


<img width="659" height="554" alt="image" src="https://github.com/user-attachments/assets/7514685c-9214-4432-bba1-11735e288d85" />

For the "no-access" folder, we are going to type "domain admins" and the Permission Level will be changed from Read to Read/Write.

<img width="638" height="550" alt="image" src="https://github.com/user-attachments/assets/adf2cbff-5efa-4ae4-9ef8-d9f293478d67" />


### Access Attempts

Inside of the client vm, run the "\\dc-1" command and then press enter

<img width="970" height="837" alt="image" src="https://github.com/user-attachments/assets/3f43f51b-124e-410d-8d65-c1788007d1c7" />

You should see the folders that we created.

<img width="850" height="582" alt="image" src="https://github.com/user-attachments/assets/1c34d45f-19d0-44d7-805f-934e83e696ed" />


Double click the "read-access" folder, and attempt to create a new folder inside by right clicking -> New -> Folder and observe what happens.

<img width="848" height="738" alt="image" src="https://github.com/user-attachments/assets/d83541a0-0c07-4b98-9d0f-d44ab4b8e605" />

Notice that you cannot create a folder because this particular folder only has read permissions for users.

If you attempt to double click on the "no-access" folder, this happens.

<img width="639" height="236" alt="image" src="https://github.com/user-attachments/assets/78d716ae-4105-4e6c-b196-62e07af806e3" />

Inside the "write-access" folder, attempt to create a new file or folder inside and observe what happens.

<img width="859" height="741" alt="image" src="https://github.com/user-attachments/assets/d80eb17e-0497-446e-a031-20ae3e4c2f7b" />


### Accounting Access


Go back to DC-1, in Active Directory, create a new Organizational Unit called "_GROUPS" and click okay

<img width="950" height="674" alt="image" src="https://github.com/user-attachments/assets/e6697590-60da-43e7-85ca-f9543dcaf465" />

<img width="538" height="463" alt="image" src="https://github.com/user-attachments/assets/1c666bf3-b05f-43fd-beae-59dafe907a03" />

Inside of the newly created "_GROUPS" folder, right click new and then click on Group.

<img width="879" height="354" alt="image" src="https://github.com/user-attachments/assets/c253c45e-0971-4467-a3a6-4970082743b8" />

Inside the Group window we'll create a new security group called “ACCOUNTANTS” and then click okay

<img width="539" height="507" alt="image" src="https://github.com/user-attachments/assets/0ba06f43-b888-452e-a37c-d93c840da979" />


On the “accounting” folder you created earlier, set the following permissions:

Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write” as shown below.

<img width="904" height="857" alt="image" src="https://github.com/user-attachments/assets/4ba0c837-cc9b-45a3-a1b7-ae1d7a90dcb9" />


Log back on to the client vm and try to access the accountants folder, you may have to refresh the window using the F5 key. Accessing the accountants folder should fail. 

<img width="647" height="242" alt="image" src="https://github.com/user-attachments/assets/a288feae-4c67-4d6d-881f-0edbb2ff7a6f" />

Log out of the client vm as the created user that we been using.

Back on the domain controller vm, make the created user a member of the “ACCOUNTANTS”  Security Group

Double click "ACCOUNTANTS" -> Members Tab -> Add -> name of user in the big white box area -> Check Names -> Ok -> Apply -> Ok

<img width="956" height="739" alt="image" src="https://github.com/user-attachments/assets/3457ae49-3e31-49fd-8a86-771461c03116" />


Sign back into the client vm like before and try to access the “accounting” share in \\dc-1\

It should look something like this

<img width="862" height="758" alt="image" src="https://github.com/user-attachments/assets/d26fb510-d675-40c0-a71a-cd5d199fbd0c" />

If you still can't access the accounting folder, you may have to sign out inside of the vm itself, and then log back in.

This the whole lab, great work! We set up Active Directory with Windows Server, Organizational Units, generated new users with Poweshell, pointed the client virtual machine to the domain controller to reflect changes than the domain admin configures, we managed Group Policy, and learned how to share permissions with different groups and users inside of an organization.  

Remember, do not forget to stop the VM!! 

![image](https://github.com/user-attachments/assets/92abfa3a-0dc5-4284-8fde-ab364f9f546d)






