### Service Unit

```
 [Unit]
 - Description=Ping a server and log it
 - Requires=network.target
 - After=network-online.target
 
[Service]
 - Type=oneshot
 - StandardOutput=append:/system-monitor/log.txt
 - ExecStart=date '+%%T'
 - ExecStart=ping -c 5 google.com

[Install]
WantedBy=multi-user.target
```
