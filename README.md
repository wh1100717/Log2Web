Log2Web
=======

Easily set a webserve watching log file and bring it on web with autobahn websocket tech.

<img src="http://wh1100717.github.io/PolyTechDocs/img/python/log2web/log2web.png">

##Intro
Log2Web is written in python including several libs like autobahn, twisted, sh, queue and threading. you can bring the log file information of your project to the web page without any change in your project. ONLY need one command and then all things will be done automatically.

Rather than using Ajax in frontend to send request to the server periodically, connecting server with WebSocket protocol would bring much more real-timing and less communication consuming. This project using the broadcasting way to send the log information to the browser client which has connected to the server. 

<img src="http://wh1100717.github.io/PolyTechDocs/img/python/log2web/log2webnoajax.png">

(From the image above u can figure out: no ajax request has been sent to the server for fetchint the log info!)

##Requirements
* Python 2.6+
* autobahn 0.7.4+
* twisted 11.1.0+
* sh

##Installation
The test environment is centOS 6.4(64bit). If there are some issues, just try to fix it.... or feel free to create an issue in this project.(Due to the chinese network, sometimes the installation may fail, just try it again or wait for a moment.)
* install python-devel `yum install python-devel`(or `sudo apt-get install python-dev`)
* update setuptool using `easy_install -U setuptools`
* install pip `easy_install pip`(pip is a cool tool for installing python libs, you can just install python lib using `easy_install xxx` or using `pip install xxx`)
* install twisted `pip install twisted`
* install autobahn `pip install autobahn`
* install dependencies `pip install sh`

##Usage
two files should be included in your log system -- server.py(which would generate a server watching the log file and broadcast the data to the browser) and log.html(it contains the html and js code which would be included in your website.)
* just step into the directory that contains the server.py and use command `python server.py log_path port`(log_path means the absolute path of the log file which you want to bring to the web; port means the server port you specified.)
* modify the log.html with your own ip address(or hostname) and port and put the code in some page of your website.
* Then, just wath the page in browser and see what will happen!
* If you want to stop the server, just use `ctrl+c` to stop it. NEVER use `ctrl+d`, there is a thread process which will not be killed in this way(well, u can use `ps -ef | grep server.py` to see whch one should be killed and then use `kill -9 process_id`. THAT is NOT recommended!).
