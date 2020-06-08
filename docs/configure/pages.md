# Customizing the Web Interface

An admin can easily customize any page as well as customizing the look & feel.
The "*MY HOUSE*" area of the main menu contains the user-defined pages. It also includes links to default pages automatically added when installing some packages.

## Definitions

* **Section**: a section groups together in the main menu one of more menu items. You may want to use sections to group access to pages which are logically linked together. When clicking on the section, it expands, showing up the associated menu items;
* **Menu Item**: a menu item is a link to a page. It shows up in the main menu under a given section and when clicked makes the associated page loading in the screen;
* **Page**: display sensors' contents to the user. A page is made up of multiple rows and every row have one or more widget (in columns)
* **Widget**: type of visualization of a given content

## How to add a new page

* log in as an admin
* open up an existing page by clicking on a random menu item of the "*MY HOUSE*" area of the main menu
* click on the "*New Page*" button in the top right of the page
* give the page a name identifier and click on "*Save*". Alphanumeric characters only, including underscores and dashes are allowed. Note down this identifier since will be needed when adding a link to the page from the main menu
* wait a few seconds until the new (empty) page is displayed. Check the URL for ensuring the newly created page has been opened
* edit the page (see bellow). please note a new page will not automatically show up in the main menu until a menu item linking to it will be added 

## How to edit a page

* click on the "*Edit Page*" button in the top right of an opened page (please note only pages from the "*MY HOUSE*" area can be edited)
* if you want to add a new row or if the page is empty, click on the "*Add Row*" button in the top right of the page
* optionally give the row a title (will be displayed just above the widgets)
* if you want to add a new widget to a row, click on the "*Add Widget*" button nearby the row title:

    * under the "*General*" tab fill in:

        * Widget Title: title of the widget, will show up on top of its content
        * Size of the Widget: how wide the widget is supposed to be, from 1 to 12 (full width). Rebember every row has a size of 12 spaces so you can add twelve widgets of size 1, two widgets of size 6, one widget of size 12, etc.
        * Widget Type: how you want to display the information. See the "*Widget Showcase*" under the "*Examples*" menu section for more details. As you select the widget type, a new tab specific for the selected type will be added in which you can configure e.g. from which sensor to pick data from, which timeseries to plot, etc. Every widget type has a different and peculiar configuration
        * Widget Offset: optionally, if you want the widget to not start from the left side of the screen, from which space has to start
    
    * under "*Permissions*" tab, leave it as it is unless you want only specific group of users to see the configured widget
    * click on "*Save*", the newly configured widget will show up in the page with live data populated in

* if needed, delete any unnecessary widgets by clicking on the trash icon in the top right corner of each widget or an entire row by clicking the "*Delete Row*" button nearby each row's title
* individual widgets and entire rows can be easily moved around along the page by dragging and dropping the icon with four arrows in the top right corner of each widget or by clicking and moving the "*Move Row*" button nearby each row's title
* when satisfied of the look and feel, click the "*Save Changes*" button in the top right corner of the page. Changes can be undone at any time by clicking on the "*Discard Changes*" button
* once saved, the old layout will still show up. Wait for a few seconds until your changes are loaded

## How to add a menu item linking to a page

* ensure you created already a page and you know the page identifier
* always as an admin, locate the "*Edit Menu*" button at the bottom of the left menu
* click on "*New Section*" if you want your page to be listed under a new section. If you want to reuse an existing section, skip this step:

    * fill in the required section information:

        * Section Identifier: give the section a name identifier. Alphanumeric characters only, including underscores and dashes are allowed. This will be used when configuring a menu item to reference this section
        * Text: enter the text of the section. This is the text that will be displayed in the main menu
        * Icon: optionally the name of the icon to display next to the text
        * Order: the order within the "*MY HOUSE*" area this section will be listed. Every section is given an order number and eGeoffrey will display the one with the lowest number first (e.g. if a section has order zero and another has order twenty, the first one will be displayed on top of the other)
    
    * click on "*Save*". Wait for a few seconds until your changes are loaded
    
* click on "*New Menu Item*" to eventually make your page accessbile from the main menu:

    * fill in the required menu item information:

        * Section Identifier: the section identifier under which you want this menu item to be associated with The section should already exist
        * Menu Item Identifier: give the menu item an identifier. Alphanumeric characters only, including underscores and dashes are allowed. 
        * Text: enter the text of the menu item. This is the text that will be displayed in the main menu
        * Page: the page identifier (should already exist) you want to open when this menu item is clicked
        * Icon: optionally the name of the icon to display next to the text
        * Order: the order within the "*MY HOUSE*" area this menu item will be listed within the section. Every menu itrem is given an order number and eGeoffrey will display the one with the lowest number first (e.g. if a menu item has order zero and another has order twenty, the first one will be displayed on top of the other)
        * Authorized Groups: leave it empty unless you want only specific group of users to see the menu item
    
    * click on "*Save*". Wait for a few seconds until your changes are loaded
    
## How to edit the main menu

* if you want to edit an existing section, always as an admin, locate the "*Edit Menu*" button at the bottom of the left menu and click on "*Edit Sections*". An edit icon is displayed nearby any section of the "*MY HOUSE*" area. Click on the section you want to edit for the wizard to show up.
* if you want to edit an existing menu item, always as an admin, locate the "*Edit Menu*" button at the bottom of the left menu and click on "*Edit Sections*". An edit icon is displayed nearby any menu item of the "*MY HOUSE*" area. Click on the menu item you want to edit for the wizard to show up.