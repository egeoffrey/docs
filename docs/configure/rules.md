# Rules

## Definition

Rules can **execute specific tasks periodically or upon specific conditions**.

A rule is defined as a **set constants (e.g. static values) and variables (e.g. values coming from sensors) combined in conditions**. **Notifications are generated whenever a configured rule triggers**. Rules can also execute additional actions (e.g. set a value to a sensor, trigger another rule, etc.)

You can see the configured rules and create new rules by accessing the web interface as an admin user and going to "*House*", "*Rules*" under "*Administration*".

## Add a new rule

To add a new rule, the process is the following:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Rules**" under "**ADMINISTRATION**". A list of existing rules will be provided;
* Click on the "**Add a New Rule**" button on top of the page. A wizard will show up. Provide the following information - anything with an asterisk is required:

    * "**General**" - general settings for the rule:
    
        * "**Rule identifier**": give the rule a name identifier. This is they way the rule can be referenced and invoked by other rules, widgets, etc. Alphanumeric characters only, including underscores and dashes are allowed;
        * "**Disabled**": check this box if you want the rule to be disabled;
        * "**Rule Text**": text of the rule when triggers. This is what will show up in the web interface under "Notifications" and what will be sent to any configured [notification modules](/configure/modules/#notifications). If you want the text can be dynamically populated with configured variables' values, use placeholders like `%variable_identifier%`
        * "**Severity**": the severity of the notification when this rule triggers. This can be used by notification modules to filter in or out specific notifications. Possible values are "Alert", "Warning" and "Info". "Debug" will generate a notification in the web interface but no notification modules will be triggered. "None" will not even generate the notification in the web interface but just produce an entry in the logs
        * "**Type**" - type of the rule:
        
            * "**Recurrent**": the rule will run based on a configured schedule. Select this option if you want this rule to execute only on a specific time like e.g. if you want to turn the lights on or off at a given time. When selected, a "Schedule" tab will show up to configure when and how often running the rule:
            
                * "**Scheduling Mode**": select either "*Interval - run the job at fixed intervals of time*" or "*Cron - run the job periodically at certain time(s) of day*"
                * "**Days/Hours/Minutes/Seconds**": fill in accordingly. If "**Interval**" was selected above, this is the frequency the rule will run, if "**Cron**" was selected, this is which time and how often to run
                
            * "**On-Demand**": run the rule manually (or when requested by the chatbot). Select this option if you want to link the rule execution with e.g. a button of the web interface or if you want to run it by asking the chatbot to do something
            * "**Realtime**": run the rule whenever one of the sensors listed in the "**Triggers**" tab is updated. Select this option if you want this rule to trigger only upon a change. For example if you want to turn the lights on when it is becoming too dark, you want to run this rule every time a light sensor is reporting a new value. After selecting this option, go to the "Triggers" tab, click on "Add Trigger" and write down the sensor identifier which will trigger the rule execution. Whenever a new value is recorded for this sensor, the rule will be evaluated. This doesn't mean a notification will trigger, it just means the conditions will be evaluated. 
            
    * "**Constants**" - if conditions are set, the rule triggers only when those are met. Conditions compare the values of variables (data stored in sensors) with constants (constant values). Conditions reference variables and constants so you need to configured them beforehand. Go to the "*Constants*" tab and click on "*Add Constant*". Give the constant an identifier (Alphanumeric characters only, including underscores and dashes are allowed) - this will be the way you can reference it in your conditions - and a value. For example set `status_on` to 1 so in your conditions you can check if the value of a sensor is on. 
    * "**Variables**" - Go to the "*Variables*" tab and click on "*Add Variable*". Give the variable an identifier (Alphanumeric characters only, including underscores and dashes are allowed) - this will be the way you can reference it in your conditions - and a sensor identifier as value. This will populate the variable with the latest value of the sensor. There are also additional, more advanced options you can leverage since the variable value can be in the format `DISTANCE|TIMESTAMP|ELAPSED|COUNT|SCHEDULE|POSITION_LABEL|POSITION_TEXT] [-<start_position>],[-<end_position>] <sensor_identifier>`. For any variable defined here a placeholder in the format `%variable_identifier%` can be used in the rule's text and will be replaced by its value when the rule triggers. Examples:

        * `alarm_status = alarm/status`: `alarm_status` will be assigned the latest value of the `alarm/status/status` sensor
        * `boiler_off_minutes = ELAPSED boiler/status`: The elapsed time in minutes since the latest measure of `boiler/status/status` will be assigned to the variable `boiler_off_minutes`
        * `latest_5_days = -5,-1 outdoor/temperature/day/avg`: The latest 5 daily averages of the sensor outdoor/temperature will be assigned to the variable `latest_5_days`

    * "**Conditions**" - if no conditions are set, when the rule is run, it will just trigger. Conditions make the rule triggering only under specific circumstances. To add a condition, go to the "Conditions" tab. Conditions can be grouped in block, each block can have one or more conditions. Conditions within the same block will be evaluated in AND (all must meet for the block to be true) whereas block are evaluated in OR (if at least one block is true, the rule triggers). Previously defined constants and variables have to be used when setting up a condition. Please note when doing a comparison, static values are not allowed, they have to be defined as constants. Once again, the rule triggers if all the conditions of a block evaluate to true (AND). If there are multiple blocks the rule triggers when at least one block evaluate true (OR). Click on "Add Block" and then "Add Condition". Here you can compare your previously set constants and variables. The condition has to be in the format `<variable_identifier|constant_identifier> [==|!=|<|>|in] <variable_identifier|constant_identifier>`.
    Single subexpressions are also allowed on both the sides of the comparison by using parentheses and one of the following operators: `+|-|*|/`. Examples:
        
        * `alarm_status == status_on`: Check if the variable `alarm_status` is equals to the constant `status_on`
        * `temperature > threshold`: Check if the variable `temperature` is higher than then constant `threshold`
        * `temperature > (threshold + delta)`: Check if the `temperature` variable is higher than the constants `threshold` summed to another constant called `delta`

    * "**Macro**" - macro is an advanced concept and not required for basic rules. If you want the same rule to be executed for multiple entities (e.g. different sensors), you can use macros without the need to write the same rule multiple times for different sensors. For example, if you want to be notified whenever the battery of multiple sensors is falling below a given threshold, you can setup a single rule and list as macros all the sensors you want to run this rule against. Go to the "*Macro*" tab, click on "*Add Placeholder*" and reference the sensor identifier. Then you can use the `%i%` placeholder in variables and actions that will be replaced with the sensor's value and the rule will be run in parallel for each instance For example:
        
        * `alarm/pir/ground_floor`: the `%i%` placeholder is made available in variables and actions and can be used for e.g. referencing other sensors like `%i%_armed` which will be expanded into `alarm/pir/ground_floor_armed`
        
    * "**Actions**" - when a rule triggers it will generate a notification without any additional configuration. This will show up in the web interface as well as any other notification module will be triggered. Optionally you may want to configure additional actions to e.g. set values to other sensors, trigger an actuator or trigger other rules. You can either `SET` a new value to a sensor, `POLL` a service associated to a sensor, `RUN` a different rule in the format `[SET|POLL|RUN] <sensor_identifier|rule_identifier> [<value>]`. Examples:

        * `SET alarm/door/first_floor_armed 1`: Set the value of the sensor `alarm/door/first_floor_armed` to 1
        * `SET irrigation/control/req 1`: Turn the irrigation on by triggering the `irrigation/control/req` actuator
        * `RUN welcome_home`: Run the rule with `welcome_home` identifier
        
## Disable a rule

You can disable a rule from running without deleting it. 

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Rules**" under "**ADMINISTRATION**". 
* A list of existing rules will be provided. Search for the rule you want to disable
* Click on the "**Actions**" button and select "Edit Rule". Check the "Disabled" box in the "General" tab and click on "Save".

## Delete a rule

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Rules**" under "**ADMINISTRATION**". 
* A list of existing rules will be provided. Search for the rule you want to disable
* Click on the "**Actions**" button and select "Delete Rule".

## Manually run a rule

To manually run a rule for e.g. testing purposes:

* Connect to the eGeoffrey web interface, as an admin user and go to "**House**", "**Rules**" under "**ADMINISTRATION**". 
* A list of existing rules will be provided. Search for the rule you want to disable
* Click on the "**Actions**" button and select "Run Rule".