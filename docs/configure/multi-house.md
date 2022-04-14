# Managing multiple houses with eGeoffrey

You may be in a situation where eGeoffrey is installed in multiple houses and you want to get access to them all somehow. 
eGeoffrey fully supports this scenario.

#### Web Interface

With the eGeoffrey web interface you can access whatever eGeoffrey instance, either the one where it is running or a different one. To do so, just point to the eGeoffrey gateway where the other house is running and you will get into it straight away. 

To facilitate switching between multiple houses, the web interface allows saving a connection for future use. When logging in and selecting the "Remember Me" checkbox makes your browser remembering the connection (e.g. the combination of username, house id, gateway and port). Saved connections can be loaded from the dropdown select at the top of the login screen. 

Additionally, once logged in, in the top of the screen just aside the name of the house, a  dropdown menu allows to select one of the previously saved connection for fast-switching into it. 

To delete a saved connection, just uncheck "Remember Me" and click the Login button.

#### Mobile App

Notifications from multiple houses can be received by the same eGeoffrey mobile App. All you have to do is to configure the `egeoffrey-notification-mobile` package in the two eGeoffrey instances to send notification to the same device identifier. The app will then notify you and the house name will show up on top of the notification which will be grouped together by the name of the house.

The Mobile App interface has the same capabilities of the web interface described above.

## Running multiple houses on the same machine

You can run multiple, independent houses on the same machine by installing eGeoffrey in two different locations of the filesystem. Just ensure in the `docker-compose.yml` file that each instance will expose their services to different ports.

## Running eGeoffrey in multiple locations

All the scenarios above imply you want to configure two fully independent houses. A different configuration could be to have the same eGeoffrey instance (e.g. same house) spread across two or more locations. 

This is once again supported as far as the eGeoffrey controller/database/gateway reside only in a primary location and the others are configured with `egeoffrey-cli config setup` to connect to the remote gateway offered by the primary location. Of course that gateway must be reachable over the network.