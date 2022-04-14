# Accessing eGeoffrey remotely

Even when you are outside of your place you can get in touch with eGeoffrey. This can be done via notifications or by fully accessing eGeoffrey web interface.

### Notifications

The notifications can reach you anywhere, also when you are outside your local network. Visit eGeoffrey's [Marketplace](https://marketplace.egeoffrey.com) to install the package you need for being notified in the way you like the most (Slack, Email, Telegram, etc.). 

Additionally, with eGeoffrey's [Mobile App](/configure/mobile), you can even get notifications in real time on your smartphone or table.

### Web Interface

You can access your eGeoffrey gateway remotely through one of the following methods (ordered from low-effort to high-effort approaches). Once the gateway is reachable from the remote location, you can access to it by either using eGeoffrey Mobile App or pointing your browser to [http://cloud.egeoffrey.com](http://cloud.egeoffrey.com).

#### VPN Access

Setup a VPN (Wireguard, OpenVPN etc.) on your Raspberry and configure a remote connection on your laptop or mobile so to access eGeoffrey like if you were at home.

#### Expose eGeoffrey Gateway to the Internet

Open port 443 on your router and make it pointing to where eGeoffrey runs. Before doing so, please ensure the gateway has both SSL and a strong password set.

####  Host an eGeoffrey Gateway in the Cloud

Setup a MQTT broker accessible from the Internet or leverage a public MQTT service (be concious sensitive information regarding your house are exchanged with this third party). Configure then your local gateway to connect to it by setting `REMOTE_EGEOFFREY_GATEWAY_HOSTNAME`, `REMOTE_EGEOFFREY_GATEWAY_PORT`, `REMOTE_EGEOFFREY_GATEWAY_SSL`, `REMOTE_EGEOFFREY_ID`, `REMOTE_EGEOFFREY_PASSCODE` with `egeoffrey-cli config env <variable> [<value>]` so to bridge the two instances.

*An additional option called eGeoffrey Cloud Gateway provided by the eGeoffrey team as a service has been suspended in April 2022*
