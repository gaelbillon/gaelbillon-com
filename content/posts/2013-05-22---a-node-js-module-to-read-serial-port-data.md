---
title: "A Node.js module to read serial port data"
date: "2013-05-22T15:26:16.000Z"
template: "post"
draft: false
slug: "a-node-js-module-to-read-serial-port-data"
category: "Uncategorized"
tags: 
  - "English"
  - "pll_5bf81c186da63"
  - "Uncategorized"
description: "Serialport is a Node.js module to read and write data on a serial port, here's a quick overview of its usage with a an APM board with Ardupilot software."
---

![node.js serialport npm sublimeText screenshot](/media/2013-05-22---a-node-js-module-to-read-serial-port-data/node.js-serialport-sublime-text-screenshot-1.png)

[Serialport](https://npmjs.org/package/serialport) is a node.js module that reads the serial port data. It opens up a lot of doors for javascript such as... switching on the living room light or... [communicate with a drone](/posts/en/portfolio-item/uav-ground-control-station-web-app-with-node-serialport/) !

Using it is pretty straightforward

`npm install serialport`

> Serialport installation requires python 2.x and Xcode command line tools For the Command line tools, no need to download the whole Xcode app (which is a few Gygabytes), you may download only the command line tools [here](https://github.com/kennethreitz/osx-gcc-installer#option-1-downloading-pre-built-binaries) 

We'll then create a server named server.js and copy the following code into. You may need to replace the baudrate, 57600 is the default baudrate for Ardupilot on APM. You will very likely need to replace `tty.usbserial-A6023L0J` with the name of your device. On macOS and GNU/Linux `ls /dev/tty.*`  to show connected devices.

The following lines in App.js are configuring and initalizing the websocket connection : 


```javascript
var io = require('socket.io').listen(server); 
io.sockets.on('connection', socket);

var serialport = require("serialport");
var SerialPort = serialport.SerialPort;
var sp = new SerialPort("/dev/tty.usbserial-A6023L0J", {
parser: serialport.parsers.readline("n"),
baudrate: 57600
});

sp.on("open", function() {
console.log('open');
sp.on('data', function(data) {
console.log('data received: ' + data);
});
});
```

Let's launch the server : `node server.js`

If an APM with Ardupilot or an equivalent device is connected to your computer, the terminal should display the console.log which looks like that :

[![node.js serialport](/media/2013-05-22---a-node-js-module-to-read-serial-port-data/Screen-shot-2013-05-30-at-11.32.53-AM.png)](/posts/wp-content/uploads/2013/05/Screen-shot-2013-05-30-at-11.32.53-AM.png)

Serialport allows you not only to read but also write data on the serial port, which let envision many possible uses. If you are interested, here are two interesting posts on the subject. The first one about controlling an Arduino with Node.js and the second one on Javascript and Robotics by the Author of the serialport module :

[http://brandontilley.com/2012/03/02/controlling-an-arduino-from-nodejs.html](http://brandontilley.com/2012/03/02/controlling-an-arduino-from-nodejs.html)

[http://voodootikigod.com/nodebots-the-rise-of-js-robotics](http://voodootikigod.com/nodebots-the-rise-of-js-robotics)
