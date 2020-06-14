# Customizing the Web Interface

An admin can easily customize any page as well as customizing the look & feel.

The "**MY HOUSE**" area of the main menu contains the user-defined pages and it is completely up to you the way you want to organize your contents. It also includes links to default pages automatically added when installing some packages.

## Definitions

* **Section**: a section groups together in the main menu one of more menu items. You may want to use sections to group access to pages which are logically linked together. When clicking on the section, it expands, showing up the associated menu items;
* **Menu Item**: a menu item is a link to a page. It shows up in the main menu under a given section and when clicked makes the associated page loading in the screen;
* **Page**: display sensors' contents to the user. A page is made up of multiple rows and every row have one or more widget (in columns)
* **Widget**: type of visualization of a given content. Typically you need to configure a sensor first and then associate it to the widget to present its values

## How to add a new page

* log in as an admin
* open up an existing page by clicking on a random menu item of the "**MY HOUSE**" area of the main menu
* click on the "**New Page**" button in the top right of the page
* give the page a name identifier and click on "**Save**". Alphanumeric characters only, including underscores and dashes are allowed. Note down this identifier since will be needed when adding a link to the page from the main menu
* wait a few seconds until the new (empty) page is displayed. Check the URL for ensuring the newly created page has been opened
* edit the page (see bellow). please note a new page will not automatically show up in the main menu until a menu item linking to it will be added 

## How to edit a page

* click on the "**Edit Page**" button in the top right of an opened page (please note only pages from the "**MY HOUSE**" area can be edited)
* if you want to add a new row or if the page is empty, click on the "**Add Row**" button in the top right of the page
* optionally give the row a title (will be displayed just above the widgets)
* if you want to add a new widget to a row, click on the "**Add Widget**" button nearby the row title:

    * under the "**General**" tab fill in:

        * "**Widget Title**": title of the widget, will show up on top of its content
        * "**Size of the Widget**": how wide the widget is supposed to be, from 1 to 12 (full width). Remember every row has a size of 12 spaces so you can add twelve widgets of size 1, two widgets of size 6, one widget of size 12, etc.
        * "**Widget Type**": how you want to display the information. See the "*Widget Showcase*" under the "*Examples*" menu section for real examples. As you select the widget type, a new tab specific for the selected type will be added in which you can configure e.g. from which sensor to pick data from, which timeseries to plot, etc. Every widget type has a different and peculiar configuration. The following options are available:
        
            * *Summary*: display the latest value of a sensor together with min/max of yesterday/today. Useful when you want to see e.g. current temperature and min/max of today and yesterday. Requires the sensor to have a numeric format and an automatic aggregation set which calculates hourly and daily statistics
            * *Value*: display the latest value of a sensor. Useful when you want to see e.g. the current temperature
            * *Timeline*: display a timeline chart. Useful when you want to see e.g. temperature averages, min/max over a timeline. Requires the sensor to have a numeric format and an automatic aggregation set which calculates hourly and daily statistics
            * *Range*: display a chart with min and max value. Useful when you want to see e.g. temperature min/max for the next few days. Requires the sensor to have a numeric format and an automatic aggregation set which calculates hourly and daily statistics
            * *Status*: display an on/off status. Useful when you want to see e.g. the status of an actuator (on/off). Requires the sensor to have a integer format and values of 0 and 1
            * *Control*: you can control an on/off switch. Useful when you want to control an actuator (on/off). Requires the sensor to have a integer format and the actuator to handle values of 0 and 1
            * *Input*: display an input box. Useful when you want to set dynamically e.g. the maximum temperature before turning automatically off the heater. Sensors can have any format depending on the use case
            * *Button*: display a button and associate actions. Useful when you want to execute one or more actions triggered manually by the user when clicking on the button. Actions may include set values to a sensor, run rules, etc.
            * *Calendar*: display a calendar for scheduling event. Useful when you want to e.g. schedule when to turn the heater or irrigation on/off automatically. Requires the sensor to have a "calendar" format and rules to evaluate if it is the time to do an action
            * *Image*: display an image stored in a sensor. Useful when you want to e.g. show a screenshot from your webcam. Requires the sensor to have a image format
            * *Map*: display a map plotting positions stored in a sensor. Useful when you want to e.g. show on a map your positions or latest earthquake around the world. Requires the sensor to have a "position" format. Before using this widget, please get a  [Google Maps API key](http://developers.google.com/maps/documentation/embed/get-api-key) and set it in "*House*", "*Settings*" under "*ADMINISTRATION*", under the "Web Interface" tab
            * *Text*: display a text statically or from a sensor. Useful for e.g. adding explanations or static text to your pages
            * *Table*: display a dynamic table. Useful when you want to e.g. show on a table the latest news from a RSS feed. Requires the sensor to have a string format. The rows of the table will be the different lines of the string (e.g. rows are split by new line character)
            * *Counter*: display a counter with the number of values stored in a sensor
            * *Tasks*: display a to-do list. Useful when you want to e.g. have a shopping list where users can add / check items on it. Requires the sensor to have a "tasks" format
            * *Notifications*: shows list of the latest notifications. It is the same table you get in the Welcome page
            * *Chatbot*: display the interactive chatbot you can ask questions regarding your sensors or trigger configured rules
            * *Slider*: display a range slider. Useful when you want to e.g. change the intensity of a smart light. 
            
        * "**Widget Offset**": optionally, if you want the widget to not start from the left side of the screen, from which space has to start
    
    * under "**Permissions**" tab, leave it as it is unless you want [only specific group of users to see the configured widget](/configure/users)
    * click on "**Save**", the newly configured widget will show up in the page with live data populated in

* if needed, delete any unnecessary widgets by clicking on the trash icon in the top right corner of each widget or an entire row by clicking the "**Delete Row**" button nearby each row's title
* individual widgets and entire rows can be easily moved around along the page by dragging and dropping the icon with four arrows in the top right corner of each widget or by clicking and moving the "**Move Row**" button nearby each row's title
* when satisfied of the look and feel, click the "**Save Changes**" button in the top right corner of the page. Changes can be undone at any time by clicking on the "**Discard Changes**" button
* once saved, the old layout will still show up. Wait for a few seconds until your changes are loaded

## How to add a menu item linking to a page

* ensure you created already a page and you know the page identifier
* always as an admin, locate the "**Edit Menu**" button at the bottom of the left menu
* click on "**New Section**" if you want your page to be listed under a new section. If you want to reuse an existing section, skip this step:

    * fill in the required section information:

        * **Section Identifier**: give the section a name identifier. Alphanumeric characters only, including underscores and dashes are allowed. This will be used when configuring a menu item to reference this section
        * **Text**: enter the text of the section. This is the text that will be displayed in the main menu
        * **Icon**: optionally the [name of the icon](/configure/icons) to display next to the text
        * **Order**: the order within the "**MY HOUSE**" area this section will be listed. Every section is given an order number and eGeoffrey will display the one with the lowest number first (e.g. if a section has order zero and another has order twenty, the first one will be displayed on top of the other)
    
    * click on "**Save**". Wait for a few seconds until your changes are loaded
    
* click on "**New Menu Item**" to eventually make your page accessible from the main menu:

    * fill in the required menu item information:

        * **Section Identifier**: the section identifier under which you want this menu item to be associated with. The section should already exist
        * **Menu Item Identifier**: give the menu item an identifier. Alphanumeric characters only, including underscores and dashes are allowed. 
        * **Text**: enter the text of the menu item. This is the text that will be displayed in the main menu
        * **Page**: the page identifier (should already exist) you want to open when this menu item is clicked
        * **Icon**: optionally the [name of the icon](/configure/icons) to display next to the text
        * **Order**: the order within the "**MY HOUSE**" area this menu item will be listed within the section. Every menu itrem is given an order number and eGeoffrey will display the one with the lowest number first (e.g. if a menu item has order zero and another has order twenty, the first one will be displayed on top of the other)
        * **Authorized Groups**: leave it empty unless you want [only specific group of users to see the menu item](/configure/users)
    
    * click on "**Save**". Wait for a few seconds until your changes are loaded
    
## How to edit the main menu

* if you want to edit an existing section, always as an admin, locate the "**Edit Menu**" button at the bottom of the left menu and click on "**Edit Sections**". An edit icon is displayed nearby any section of the "**MY HOUSE**" area. Click on the section you want to edit for the wizard to show up.
* if you want to edit an existing menu item, always as an admin, locate the "**Edit Menu**" button at the bottom of the left menu and click on "**Edit Sections**". An edit icon is displayed nearby any menu item of the "**MY HOUSE**" area. Click on the menu item you want to edit for the wizard to show up.

## I want to see a different page upon login

If you already logged in eGeoffrey, next time you access the web interface, the browser will remember your credentials and the last page you were visiting. 

But if you are a new user or accessing from a different browser/device, the "Welcome" page is presented by default. If you want new users to see a different page, go to "*House*", "*Settings*" under "*ADMINISTRATION*", click the "Web Interface" tab and set in "Default Page" the page identifier of the page you want to be presented when accessing the web interface