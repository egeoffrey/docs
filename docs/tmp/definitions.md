# Definitions

eGeoffrey calls things the way it was taught in the e-butler school back in time, and this section will introduce you to some of these concepts on the go. 

### Sensor
A *sensor* is a kind of *virtual notebook* where eGeoffrey write things down to remember what is going on and, when we ask any question, it’s used to display information, trigger an alert to keep us aware of something or whatever we want eGeoffrey to do for us. 

*Sensors/e-notebooks* range from those with naive functionality such as task lists or city weather conditions to more sophisticated ones such as those tracking what IoT home devices are measuring.

More technically, in eGeoffrey a sensor is defined as a dataset, a logical container of one or more values.

 * it can hold just a single piece of data or a timeseries
 * Sensor's values can come from an associated service (e.g. a url with an image, a command to run, etc.), from actions triggered by a rule or from your interaction with widgets on the web interface
 * a sensor is made of an `id` (e.g. the way the user references it) and additional information like retention policies, associated services, etc.
    
First thing you need to do when you want to add additional data into eGeoffrey is adding a new sensor and associating it to a service. A sensor without a service associated is just a place where the user can store data (e.g. by acting on the web interface widgets or populated by a rule).

You can see the configured sensors and create new sensors by accessing the web interface as an admin user and going to "*House*", "*Sensors*" under "*Administration*".

### Module
A module is defined as a functional unit. Every service is a module and eGoeffrey itselft is made of a different modules. There are different kind of modules:

 * `controller`: modules part of the eGeoffrey core (e.g. interact with the database, collect data from sensors, run alerting rules, etc.)
 * `interaction`: modules responsible for interacting with the user (e.g. through Slack, a microphone, etc.)
 * `notification`: modules responsible for notifying the user about something (e.g. through email, slack, text messages, etc.)
 * `service`: modules responsible for interfacing with a specific device or protocol to retrieve data or control actuators (e.g. a weather service, a webcam, a MySensors device, Zigbee protocol, etc.)
 * `gui`: modules responsible for running the eGeoffrey GUI

Modules' naming convention is `<module_type>/<module_name>`.
You can see the installed modules by accessing the web interface as an admin user and going to "*eGeoffrey*", "*Modules*" under "*Administration*".

#### Service
A *service* (a special kind of module) represents something eGeoffrey is capable of and that, eventually, will end up in a *sensor/e-notebook* for further use. A very *simple service/capability* might be one accessing an online weather service to get weather conditions for your city, which will be written down in a *sensor/e-notebook* to finally display it in eGeoffrey’s user interface. 

Of course, there are more elaborated services such as those pulling images from webcams and keeping us informed of what’s going on at home when we are away.

Before associating a service to a sensor, you must install the service (e.g. functionality) you need. Many sensors can be associated to the same service (with a different configuration).

### Package
A package is defined as one or more modules built together. It may also include sample sensors, rules or pages. Packages is what you can find in the eGeoffrey's Marketplace. When you run e.g. `egeoffrey-cli install egeoffrey-service-weatherchannel`, you are installing a package,  containing one or more modules (in this case only the module called `service/weatherchannel`.

You can see the installed packages by accessing the web interface as an admin user and going to "*eGeoffrey*", "*Packages*" under "*Administration*".

## Web Interface

Is the main way you can interact with eGeoffrey, configure your sensors and perform other admin tasks. All the configuration can be performed through the web interface (but installing new components and updating eGoeffrey which is done with the CLI). 




## CLI

Upon installation a command line utility  called `egeoffrey-cli` is also installed. This makes a number of complex tasks trivial for an eGeoffrey admin.

Admins can leverage it for installing new eGeoffrey packages, starting/stopping eGeoffrey's components, searching for new packages in the marketplace, updating the software, etc.

Developers can leverage it for committing changes to their modules or building the Docker image of their packages.

## Rule

Rules can execute specific tasks perdiocally or upon specific conditions.
A rule is defined as a set constants (e.g. static values) and variables (e.g. values coming from sensors) combined in conditions. Notifications are generated whenever a configured rule triggers. Rules can also execute actions (e.g. set a value to a sensor, trigger another rule, etc.)

You can see the configured rules and create new rules by accessing the web interface as an admin user and going to "*House*", "*Sensors*" under "*Administration*".

## User

## Group


### Widget



## Notification

