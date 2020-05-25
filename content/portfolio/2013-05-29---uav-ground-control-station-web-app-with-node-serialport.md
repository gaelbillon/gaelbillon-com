---
title: "UAV Ground Control Station web app with Node Serialport"
date: "2013-05-29T13:01:49.000Z"
template: "portfolio"
draft: false
slug: "uav-ground-control-station-web-app-with-node-serialport"
category: "Portfolio"
tags: 
  - "English"
  - "Mobile applications"
description: "A Ground Control Station for drones using Node.js Serialport module and MAVLink protocol. Made with HTML5, CSS3, Angular.js, Node.js & websockets."
---

\[av\_one\_full first av\_uid='av-lefhm'\]

\[av\_textblock size='' font\_color='' color='' av-medium-font-size='' av-small-font-size='' av-mini-font-size='' av\_uid='av-dlgiq' admin\_preview\_bg=''\] [![Nodejs_websockets__angular_mavlink_ground-control-station](/media/portfolio/2013-05-29---uav-ground-control-station-web-app-with-node-serialport/Nodejs_websockets__angular_mavlink_ground-control-station-495x400.jpg)](/posts/wp-content/uploads/2013/05/Nodejs_websockets__angular_mavlink_ground-control-station.jpg)This application is a GCS short for Ground Cotrol Station. It receives and display flight informations for an unmanned aircraft.

The application opens a websocket connection between the client (a web browser) and the server, the connection stays open afterwards and the server can push informations. The clientthe client does not need to poll the server every X seconds to get updated flight informations.

[![radio-telemetry-kit-433mhz](/media/portfolio/2013-05-29---uav-ground-control-station-web-app-with-node-serialport/radio-telemetry-kit-433mhz.jpg)](http://store.3drobotics.com/products/3dr-radio-telemetry-kit-433-mhz)Flight informations are read from the serial port with the Node.js module named [Node Serialport](https://www.npmjs.com/package/serialport) . The Serialport module read data from a 433 MHz telemetry module as the one shown above.

The informations received on the serial port can then be parsed with the help of another node [module named Mavlink](https://npmjs.org/package/mavlink)  which helps to decode the messages received in [Mavlink](http://qgroundcontrol.org/mavlink/start) (a communication protocol for drones).

The flight informations can then be displayed and updated in real time on the web interface thanks to [Angular.js](/posts/outils-et-frameworks/#angular) two way data-binding which automatically update the view when new data are available.

CSS3 transition are used are used to display a compass without resorting to heavy javascript animations. On the following line : _div(class='compass', style='-webkit-transform:rotate({{heading}}deg)')_ _{heading}_ is a Mavlink message recevied from the serial port.

This app is usable but has only been developed for the purposes of education and enjoyment and as a proof of concept so as to show what can be done with the latest web technologies. (This original text in french was written in may 2013, so yes, websockets were the latest cool web technology ;) ) This app would need a lot more work to become a real GCS but it can be used without any problem as it only receive and display informations and never send anything to the drone. Please do not hesitate to fork this project on [GitHub.](https://github.com/gaelbillon/Nodejs-Websockets-GCS)

This app could easily be extended to arm and disarm the motors, create missions with waypoints and write them on the Ardupilot board or even use accelerometers on a tablet to pilote a drone with the help of the "Device orientation API". \[/av\_textblock\]

\[av\_button label='Check out the project on GitHub' link='manually,https://github.com/gaelbillon/Nodejs-Websockets-GCS' link\_target='\_blank' size='medium' position='center' label\_display='' icon\_select='yes' icon='89' font='entypo-fontello' color='blue' custom\_bg='#444444' custom\_font='#ffffff' av\_uid='av-95pqy' admin\_preview\_bg=''\]

\[/av\_one\_full\]
