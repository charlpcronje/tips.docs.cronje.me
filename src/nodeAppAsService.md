# How to run a `node.js` app as a background service ?

`Node.js` is a platform built on Chrome’s JavaScript v8 engine, which is used for easily building fast and scalable network applications, javascript uses an event-driven, non-blocking I/O model that makes it lightweight and efficient which is perfect for data-intensive real-time applications that run across distributed devices and to make use of the tools (or packages) in Node. js, we need to be able to install in our machine and manage them in a useful way.

To run a `node.js` app as a background service is to even after closing the node terminal, the app server needs to be kept running.

## Methods to run `node.js` app as background service

**Method 1:** The easiest method to make a `node.js` app run as a background service is to use the forever tool. The forever is a simple Command Line Interface Tool that ensures that a given particular script runs continuously without any interaction.

Command for Installation: The following command installs the forever tool in the app.

```shell
npm install forever -g
```

Command to Start forever: To start the forever tool, run the following commands replacing `<app_name>` with the name of the node.js app.

```shell
forever start /<app_name>/index.js
```

Command to Start forever: To start the forever tool, run the following commands replacing `<app_name>` with the name of the node.js app.

```shell
forever start /<app_name>/index.js
```

**Method 2:** The second method involves create a service file and manually starting the app and enabling the service to keep it running in the background.

- **Step 1:** Create a new file `<app_name>`.service file replacing `<app_name>` with the name of the node.js app. Inside the files, enter the following values:

```conf
ExecStart=/var/www/<app_name>/app.js
Restart=always
User=nobody
Group=nogroup
Environment=PATH=/usr/bin:/usr/local/bin
Environment=NODE_ENV=production
WorkingDirectory=/var/www/<app_name>
```

- **Step 2**: After configuring the service file,

Copy the `<app_name>`.service file into the `/etc/systemd/system`

Step3: Start the app with the following command to make it run with the service file:

```shell
systemctl start `<app_name>`
```

**Method 3:** Another method which can be used to run a node.js app as a background by using `nohup`. The `nohup` is another Command Line Interface Tool which can be used to run a node.js app as a background service.

Run the following command to start the `nohup` replacing the <app_name> with the name of the node.js app:

```shell
nohup node /<app_name>/index.js &
```

The `nohup` command does not terminate this process even then the command terminal is closed.
