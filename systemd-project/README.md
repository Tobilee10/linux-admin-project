# TITLE: **Custom Systemd Service Management**

## **PROJECT OVERVIEW**

This project demonstrates how to create, configure, and manage custom servicecs using systemd. The project shows how Linux administrators automate processes, control service startup, and monitor system services which include:

- Creating a custom service
- Automatically starting service on boot
- Managing services using systemctl
- Logging with journald
- Troubleshooting services

## Tools Used

- Linux (AWS Instance Ubuntu)
- systemd
- systemctl
- journalctl

### step1: Create a Systemd Service File

    sudo nano /etc/systemd/my-network-monitor.service

    mkdir network-log/log.txt
![step1]()

### step2: Reload Systemd

    sudo systemctl daemon-reload
    
![step2]()

### step3: Start the Service

    sudo systemctl start my-network-monitor.service

    sudo systemctl status my-network-monitor.service

![step3](./images/start-network-service.png)

### step4: Enable Service at Boot

> sudo systemctl enable my-network-monitor.service
![step4](./images/enable-network-service.png)

### step5: View Logs

    journalctl -u my-network-monitor.service
![journal](./images/journal2.png)
   

### step6: Troubleshooting

    sudo systemctl status my-network-monitor.service

![troubleshoot](./images/start-network-service-error.png)

    sudo journalctl -u my-network-monitor.service

![troubleshoot](./images/journal1.png)

### Issue Faced: misconfig, and errors

> Service failed to start: 

![](./images/Screenshot%20from%202026-03-10%2012-32-31.png)
![typo-Error](./images/typo-error.png)

![network-Error2](./images/network-status-error.png)

> systemctl status my-network-monitor.service

![status-message]()

> sudo systemctl edit --force --full my-network-monitor.service


### Solution1: **Corrected the error by typing space between ping and -c save and exit.**

![typo-correction](./images/typo-correction.png)


### Solution2:**Corrected the error by creating a network-log in / directory (/network-log) **
```
mkdir /network
systemctl start my-network-monitor.service
systemctl status my-network-monitor.service
```
![network-correction](./images/network-correction.png)

### Reconfigure the unit

> sudo systemctl daemon-reload

    sudo systemctl enable my-network-monitor.service
    sudo systemctl start my-network-monitor.service
    cat /network-log/log.txt

![network-output](./images/nano-network.png)


### Definition of Command Used

- [x] `systemctcl:` used to control the system and service manager(start, stop, status, enable or disable services).
- [x] `journalctl:` used to query and view logs collected by systemd-journald daemon.
- [x] `nano:` command-line text editor
- [x] `mkdir:` make directory

### What I Learned
- [x] Service management
- [x] Service monitoring
- [x] System troubleshooting 
