# systemd

## References
- [Understanding Systemd Units and Unit Files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files#types-of-units)
- [Systemd Essentials: Working with Services, Units, and the Journal](https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal)
- [Create a Custom systemd Service](https://www.linode.com/docs/quick-answers/linux/start-service-at-boot/)

---
## Sample commands
Using 'zerotier-one' service for example:

    sudo systemctl start zerotier-one.service
    sudo systemctl stop zerotier-one.service
    sudo systemctl restart zerotier-one.service
    sudo systemctl enable zerotier-one.service
    sudo systemctl disable zerotier-one.service
    sudo systemctl status zerotier-one.service

### List all loaded services
    systemctl list-units

### Show started service
    service --status-all

### Viewing a service (debug) log
    sudo journalctl -u zerotier-one

### View the service config (unit) file
    systemctl cat zerotier-one

### Daemon reload (after modified service file)
    sudo systemctl daemon-reload

---
## Create simple service

Create service file:

    sudo pico /usr/bin/myservice.sh

Edit service file (sample):
```sh
#!/bin/bash
echo "Starting the DroneKit SITL Copter 3.3"
dronekit-sitl copter-3.3 --home=22.317990, 114.200653,10,0
echo "Started"
exit 0
```

Make it exe:

    sudo chmod +x /usr/bin/myservice.sh

Create unit file:

    sudo pico /etc/systemd/system/myservice.service

Edit:
```conf
[Unit]
Description=My service

[Service]
Type=simple
ExecStart=/bin/bash /usr/bin/myservice.sh

[Install]
WantedBy=multi-user.target
```
Start (test it before enable):

    sudo systemctl daemon-reload
    sudo systemctl start myservice
    sudo systemctl status myservice

Enable:

    sudo systemctl enable myservice

Show error log:

    sudo journalctl -u [unit]