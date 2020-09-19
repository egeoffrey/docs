# Sensors

## Definition

A *sensor* is a kind of *virtual notebook* where eGeoffrey write things down to remember what is going on and, when we ask any question, it’s used to display information, trigger an alert to keep us aware of something or whatever we want eGeoffrey to do for us. *Sensors* range from those with naive functionality such as task lists or city weather conditions to more sophisticated ones such as those tracking what IoT home devices are measuring.

More technically, in eGeoffrey a sensor is defined as a **dataset, a logical container of one or more values**.

 * it can hold just a single piece of data or a timeseries;
 * Sensor's values can come from an associated service (e.g. a url with an image, a command to run, etc.), from actions triggered by a rule or from your interaction with widgets on the web interface;
 * a sensor is made of an `id` (e.g. the way the user references it) and additional information like retention policies, associated services, etc.
    
First thing you need to do when you want to add additional data into eGeoffrey is adding a new sensor and associating it to a service. **A sensor without a service associated is just a place where the user can store data** (e.g. by acting on the web interface widgets or populated by a rule).

You can see the configured sensors and create new sensors by accessing the web interface as an admin user and going to "*House*", "*Sensors*" under "*ADMINISTRATION*".

## Add a new sensor

To register a new sensor with eGeoffrey, the process is the follow:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". A list of existing sensors will be provided;
* Click on the "**Register New Sensor**" button on top of the page. A wizard will show up. Provide the following information - anything with an asterisk is required:

    * "**General**" - general settings for the sensor:
    
        * "**Sensor identifier**": give the sensor a name identifier. This is they way the sensor will be referenced by rules, visualization, etc. Alphanumeric characters only, including underscores and dashes are allowed;
        * "**Disabled**": check this box if you want the sensor to be disabled; disabled sensors will not be considered by the associated services;
        * "**Sensor Description**": optional short description for the sensor;
        * "**Sensor Icon**": optional [name of the icon](/configure/icons) when displaying the sensor in the list of sensors
        
    * "**Data**" - settings related to the data stored by this sensor:
        * "**Format**": the format the data to be stored in this sensor is expected to have (e.g. integer, float, string, image, etc.). This is entirely dependent on the service that will be associated with this sensor. Whenever possible, the input value is normalized before being saved (e.g. if the format is integer and the input value is 2.67, the value that will be saved will be 2). You can choose between:
            * *Integer*: if you expect an interger value or if the sensor is a on/off switch (with values 1 or 0)
            * *Float w/ one decimal*: if you expect an float value with one decimal (e.g 2.5)
            * *Float w/ two decimal*: if you expect an float value with two decimal like (e.g. 2.56)
            * *String*: if you expect a string value (e.g. "cloudy")
            * *Calendar*: to associate with a [calendar widget](/configure/pages/#how-to-edit-a-page) in the web interface for scheduling events
            * *Image*: if the value is an image. Typically associated with modules returning images like egeoffrey-service-image
            * *Position*: if the value is a a GPS position. Typically associated with modules returning GPS position like egeoffrey-service-earthquake
            * *Tasks*: to associate with a [Tasks - to do list widget](/configure/pages/#how-to-edit-a-page) when added to the web interface

        * "**Unit**": optionally the unit of measure for the data of this sensor. Will be used in notifications and in visualizations as a suffix to the value (e.g. ppm)
        * "**Minimum Value**": optional filter to avoid invalid data to be stored. When set, data below this value will be silently discarded;
        * "**Maximum Value**": optional filter to avoid invalid data to be stored. When set, data above this value will be silently discarded;
        * "**Allowed Values**": optional filter to avoid invalid data to be stored. When set, data different than provided list comma separated will be silently discarded;
        
    * "**Processing**" - configuration of any automatic processing of the data:
        * "**Automatic Aggregation**": if eGoeffrey has to perform any automatic aggregation of the data. For example if you want to automatically calculate every hour/day average, minimum and maximum values for a timeseries dataset. If not set, no aggregation of the data will be performed. Please keep in mind if you want to display [timeseries data in a widget](/configure/pages/#how-to-edit-a-page) you would need to configure an aggregation;
        * "**Retention Policies**": for how long you want eGeoffrey to store the data in this sensor. E.g. retain values for 5 days, hourly averages for 5 days and daily averages forever (ideal for timeseries) or retain the latest value only (ideal for actuators, status indicators, etc.). For any sensor for which you are interested in the latest value only, please set a retention policy to keep only this value, for any sensor storing timeseries data, please ensure you set an appropriate  retention policy as well to avoid the database to grow indefinetely;
        * "**Convert acquired value before being saved**": if the value has to be normalized or converted before being saved (e.g. the service associated can only return a temperature in Celsius and you need to visualize it in Fahrenheit etc.);
        * "**Convert input value before being sent to an actuator**": if the sensor is an actuator and the value to be sent through the associated service has to be normalized or converted before being sent (e.g. the actuator can only handle strings "ON" and "OFF" but the sensor is storing integers like 0 and 1);
        
## How sensors data gets populated

There are different ways through which sensors data get populated:

1. By [associating a sensor to a service](#associate-a-sensor-to-a-service)
1. By setting manually the [value through the web interface](#manually-set-the-value-to-a-sensor)
1. By associating the sensor to a [web interface widget](/configure/pages) and interacting with it
1. By [running a rule](/configure/rules) whose action set a value to the sensor

## Associate a sensor to a service

A sensor without a service associated will just sit there and expect data to be set somehow. But when sensors really come to life is when they are associate to a service which will pull automatically data in or will help interacting with other external devices (e.g. actuators). 

While registering a new sensor or editing an existing one, go and click to the "**Service**" tab and do the following:

* Under "**Associated Service**", select the service you want to associate the sensor with. Please note only running services will show up in the list;
* Once selected, a new input called "**How to interact with the service**" will show up. Depending on the service capabilities, you can interact with one or more of the following ways:

    * "**Pull**": periodically pull the sensor for new data. This applies for example for passive sensors you have to poll or weather service you have to actively query. When selected a new tab called "**Schedule**" will show up for configuring how to poll:
    
        * "**Polling Mode**": select either "Interval - run the job at fixed intervals of time" or "Cron - run the job periodically at certain time(s) of day"
        * "**Days/Hours/Minutes/Seconds**": fill in accordingly. If "**Interval**" was selected above, this is the frequency to poll for new data, if "**Cron**" was selected, this is which time and how often to poll

    * "**Push**": the sensor will periodically provide new data. This applies for example for active sensors waking up and providing new data periodically based on their configuration. eGeoffrey just has to sit down, wait for new data and register it. 
    * "**Actuator**": this sensor is indeed an actuator so we do not expect new data to come in but when we set a value to the sensor this is also sent by the module to the physical actuator (e.g. we set 1 to the sensor and the relay turns on)
    
* How the sensor has to behave with the service can be configured in the "**Configuration**" tab. A valid service and mode have to be selected before this tab shows up. The configuration screen will be service-dependant. Typically here you will provide e.g. the latitude, longitude and the weather information you want to store like humidity, the node_id, child_id and type of the MySensors sensor to be associated with, etc.

## Get the latest value stored by a sensor

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**Refresh**". The latest value and timestamp will appear shortly in the right side of the row;

## Manually set the value to a sensor

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**Set Value**". An input prompt will show up. 
* Set the value you want to set and click "**Ok**"
* The new value will then show up on the right side of the row;

## Show recent and historical data stored by a sensor

Especially if a sensor is storing a timeseries and automatic aggregation is running on a hourly and daily base, you may be interested in having a look at recent and historical data without necessarily build an ad-hoc page. 

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**History**". An page showing up latest values, hourly and daily timeseries will be presented;

## Delete a sensor

If you want to delete a sensor and all the data associated with it:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**Delete**";

If you instead want to delete any data stored by the sensor but keep the sensor itself:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**Reset**";

## Manually apply retention policies

If you want to manually apply retention policies after e.g. having changed it:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Sensors**" under "**ADMINISTRATION**". Search for a specific sensor;
* Click on the "**Actions**" button and select "**Purge**";