# User Management

Generally speaking there are two level of authentication to access eGeoffrey:

* **House ID and Passcode - used to authenticate against the eGeoffrey gateway**. Every user of the same house shares the same house id and passcode. Defaults are "house" house ID and no password. This additional level of authentication is useful only when hosting multiple houses in the same eGeoffrey instance
* **Username and password - to access the web interface**. By default the following two users are configured:
    
    * `guest` / `<no password>`: guest user
    * `admin` / `admin`: admin user
    
The first time a user connects to the eGeoffrey web interface, it is by default logged in as a guest user. The browser will remember the credentials (and the page) lastly used;

**Managing users is not strictly required** in eGeoffrey so if you are a first-time user, ignore this page. But in case you want to prevent anonymous users to access your eGeoffrey or give different users access to different pages, you can start exploring these functionalities. 

This help page covers only user management for the web interface, not the one at the gateway level which is a more advanced topic and not relevant for most of the users. 

## Definitions

* **User**: a user is who is accessing the web interface. Users can belong to one or more groups
* **Group**: a group is what ACLs (Access Control List) leverage to e.g. restrict access to specific pages or widgets to users belonging to that group. Users can belong to one or more groups. The following default groups are provided:

    * "**guests**": guest users can access the entire web interface but not the administration pages
    * "**house_admins**": house admins can access the entire web interface and also the "*House*" menu under "*ADMINISTRATION*" to manage the house, register new sensors, create new rules
    * "**egeoffrey_admins**": eGeoffrey admins can access the entire web interface, the "*House*" menu as well as the "*eGeoffrey*" menu under "*ADMINISTRATION*" for configuring installed packages and modules, reviewing the logs, gain insight of the database and gateway.

## How to add a new user

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Users**" under "**ADMINISTRATION**". 
* Click on the "**Users**" tab 
* Click on "**New User**" button
* Type in the username of the new user then click on "Ok"
* The new user will show up, ready to be configured. Fill in the following information:
    
    * "**Fullname**": type in name and surname of the user. This will be just the name showing up in the top left of the page once logged in, just above the menu
    * "**Icon**": [name of the icon](/configure/icons) to associate to the user. This will show up just aside the name in the top left of the page, just above the menu. If usure, type in "user"
    * "**Password**": optional password for the user to login

* Click on the "Save" button

## How to add a new group

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Users**" under "**ADMINISTRATION**". 
* Click on the "**Groups**" tab 
* Click on "**New Group**" button
* Type in the username of the new group then click on "Ok"
* The new group will show up, ready to be configured
* Click on the "**New User**" button to add a user to the group. The username should already exist
* Click on the "Save" button

## How to delete an existing user/group

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Users**" under "**ADMINISTRATION**". 
* Click on the "**Users**" or "**Groups**" tab 
* Select the user/group you want to delete
* Click on the "**Delete User**"/"**Delete Group**" button
* Click on the "Save" button
    
## How to restrict access to a given page

Image you want to have access to a specific page but don't want the rest of your family to do so. What you need to do is the following:

* Configuring different users to belong to different groups. You can use the existing users/groups or create new custom users/groups
* As an admin,go to "**House**", "**Menu**" under "**ADMINISTRATION**"
* Select the menu item you want to apply the ACL to, click on "Actions" then on "Edit"
* Under "**Authorized Groups**" click on "**Add Group**"
* Type in the name of the group you want this page to be visible and accessible; multiple groups can be added. If none are listed (the default) every group will be able to access the page
* Click on the "Save" button and wait for a few seconds for the configuration to be applied. Now only when logged in with a user belonging to one of the authorized group the menu item will be visible

## How to restrict access to a given widget in a page

Image you want only some users to see specific widgets of a given page. What you need to do is the following:

* Configuring different users to belong to different groups. You can use the existing users/groups or create new custom users/groups
* As an admin, open up the page containing the widget you want to restrict access to, click on "**Edit Page**" button at the top right of the page and then the edit button in the top right of the widget you want to configure
* Click on the "**Permissions**" tab
* Under "**Authorized Groups**" click on "**Add Group**"
* Type in the name of the group you want this widget to be visible; multiple groups can be added. If none are listed (the default) every group will be able to access the widget
* Click on the "Save" button and wait for a few seconds for the configuration to be applied. Now only when logged in with a user belonging to one of the authorized group the widget will be visible

## How to prevent anonymous login

By default, if a guest user without a password exists, when accessing eGeoffrey's web interface, access is granted. If you want any user to login (with or without a password), delete or set a password to the "guest" user.