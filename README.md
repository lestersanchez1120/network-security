# network-security

Create some sample file shares with various permissions
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as a normal user (mydomain\<someuser>)
On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”
Set the following permissions (share the folder) for the “Domain Users” group:
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
(Skip accounting for now)

Attempt to access file shares as a normal user
On Client-1, navigate to the shared folder (start, run, \\dc-1)
Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?

Create an “ACCOUNTANTS” Security Group, assign permissions, an test access
Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”
On the “accounting” folder you created earlier, set the following permissions:
Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”
On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 
Log out of Client-1 as  <someuser>
On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group
Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1\ - Does it work now?
