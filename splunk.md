# good install references for Splunk
https://gist.github.com/amanualt/beb51aeb3c971bfc6dde0549423439c9
https://answers.splunk.com/answers/625838/how-do-i-script-install-splunk-702-on-centos-7-64.html
https://splunkersayswhat.com/2018/05/31/firewalld-and-se-linux-and-splunk-oh-my/

# Install Splunk
[](https://linoxide.com/monitoring-2/install-splunk-centos-7/)
[](https://gist.github.com/stamler/e000addbe8c34c7c3d87#file-install_splunk-sh-L33)

### Create a Splunk User
- I created a user to run this application and created an application folder for the installation
```bash
# groupadd splunk
# useradd -d /opt/splunk -m -g splunk splunk
# su - splunk
```
- look bit
```bash
# getconf LONG_BIT
```
- Download Splunk Enterprise version [here](https://www.splunk.com/en_us/download.html) or wget
```bash
# wget https://download.splunk.com/products/splunk/releases/7.0.0/linux/splunk-7.0.0-c8a78efdd40f-Linux-x86_64.tgz
# tar xvf splunk-7.0.0-c8a78efdd40f-Linux-x86_64.tgz
# cp -r splunk/ /opt
# chown -R splunk: /opt/splunk/
```
### Firewall mods
- Allow web access on port tcp 8000, syslog on udp 5514
```bash
# firewall-cmd --zone=public --permanent --add-port=8000/tcp
# firewall-cmd --zone=public --permanent --add-port=5514/udp
```
- Reload firewall
```bash
# firewall-cmd --reload
```

### Run Splunk
- Splunk Installation
```bash
# su - splunk
$ cd bin/
$ ./splunk start --accept-license
```
- Now you can access your Splunk Web interface at http://IP:8000/ or http://hostname:8000
