# Modules

## Definition

A module is defined as a functional unit. Once you install a package, it provides one or more modules. eGoeffrey itselft is made of a different modules. There are different kind of modules:

 * `controller`: modules part of the eGeoffrey core (e.g. interact with the database, collect data from sensors, run alerting rules, etc.)
 * `interaction`: modules responsible for interacting with the user (e.g. through Slack, a microphone, etc.)
 * `notification`: modules responsible for notifying the user about something (e.g. through email, slack, text messages, etc.)
 * `service`: modules responsible for interfacing with a specific device or protocol to retrieve data or control actuators (e.g. a weather service, a webcam, a MySensors device, Zigbee protocol, etc.)
 * `gui`: modules responsible for running the eGeoffrey GUI

Modules' naming convention is `<module_type>/<module_name>`.

You can see the installed modules by accessing the web interface as an admin user and going to "*eGeoffrey*", "*Modules*" under "*ADMINISTRATION*".

## Configure the newly installed module

To configure a module, which may be required after installing a new package, the process is the follow:

* Connect to the eGeoffrey web interface, as an admin user and go to "*eGeoffrey*", "*Modules*" under "*ADMINISTRATION*". Find the module(s) provided by the package just installed;
* Ensure the module is running and the ping is low (not red);
* If the module does not show up as "*Configured*", it means there are mandatory settings not configured yet;
* Click on "*Actions*", "*Edit Configuration*" and fill in the required inputs. Any mandatory setting is marked with an asterisk. Click on "*Save*";
* Refresh the page, if the module was not configured, it should appear as configured now (green check). You can go back and edit the configuration of the module at any time, it will apply straight away;
* From the same page you can stop, start or restart any module by clicking on the "*Actions*" button and selecting the appropriate action;

Let's now dig into two special kind of modules: service and notification modules.

## Services

A *service* (a special kind of module) represents something eGeoffrey is capable of and that, eventually, can be associated to a *sensor* for further use. A very *simple service/capability* might be one accessing an online weather service to get weather conditions for your city, which will be written down in a *sensor* to finally display it in eGeoffrey’s user interface. 

Of course, there are more elaborated services such as those pulling images from webcams and keeping us informed of what’s going on at home when we are away.

Once a service is associated to a sensor, it can be used for either pulling information in (eventually stored in the sensor) or for interacting with external devices like actuators.

## Notifications

A *notification* is a special kind of module used by eGeoffrey to notify you about something. The approach is simple. Any informational, warning or alert notification generated by a configured rule, will be dispatched throughout any notification module configured. Of course you can configure exceptions and additional settings.

### Test a notification module

First thing you want to do once the package is installed and the notification module is configured and running, is testing if it is working correctly:

* Connect to the eGeoffrey web interface, as an admin user and go to "*eGeoffrey*", "*Modules*" under "*ADMINISTRATION*". Find the notification module you want to test and ensure it is running and it is configured;
* Click on "*Actions*", "*Send Notification*" and type in a test message and click on "*Ok*". The notification will be handled by the module and you should receive it (by email, SMS, Slack etc. depending on the notification module you are testing;

### Configure notification settings

Notification modules have special settings. In addition to the configuration required for making the module running and set e.g. recipients and other settings, there are additional configuration you can perform to e.g. filter out only specific notifications or prevent to be notified in specific timeframes. To access those settings:

* Connect to the eGeoffrey web interface, as an admin user and go to "*eGeoffrey*", "*Modules*" under "*ADMINISTRATION*". Find the notification module you want to test and ensure it is running and it is configured;
* Click on "*Actions*", "*Edit Configuration*" and switch to the "*Notification Settings*" tab;
* Tune the parameter in the way you prefer. By default you will be notified through any notification mechanism configured at any time and with any severity:

    * *Ignore notifications if below this severity*: if e.g. you want to receive the notification only for alerts, type in "alert". If empty any notification (info, warning, alert) will be dispatched through this module;
    * *Mute notifications in the following timeframe (e.g. during the night)*: if you want to mute notification off during a specific timeframe. E.g. type in "22-07" if you don't want notifications from 22:00 to 07:00. Please note those notifications will always show up in the notification panel but will not be sent out through the specific module;
    * *Even if in a muted timeframe, still accept notifications above this severity*: this is for overriding the configuration just above for specific severity. If for example you want to mute any notification BUT you want to receive alerts only during the timeframe set, type in "alert" (valid values are "warning" and "alert")
    * *Maximum number of notifications from this module to receive each hour*: to prevent too many notifications from happening, set the maximum number of notifications to be sent for each hour. When the threshold is reached, no more notifications will be sent until we turn into the next hour;
    
## Debugging a module

To enable/disable debug output of a given module do the following:

* Connect to the eGeoffrey web interface, as an admin user and go to "*eGeoffrey*", "*Modules*" under "*ADMINISTRATION*". Find the module you want to enable/disable debug output and check/uncheck the box under "*Debug*". There is no need to restart the module for the configuration to be applied.
    
## Uninstall a module

To uninstall a module you have to uninstall the package providing that module.