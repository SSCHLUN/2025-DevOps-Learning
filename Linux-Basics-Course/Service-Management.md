### What I Learned

# Creating a SYSTEMD Service

* You have to create system services in /etc/systemd/system/file.service
  - We can define a > Description=What My Service Does
  - Documentation=link to documentation.
  - If you need to start after another event occurs like a db service run > After = sqldb.service
  - defined in this file as ExecStart = /bin/shell /usr/bin/file.shell
  - You can also define it per account so users and services can have these > User=service_name
  - Define restarting functions for the service beyond start up > Restart=on-failure
  - Define restarting intervals with > RestartSec = 10 
  - you can define this on a run level basis bu adding underneath > WantedBy level.target
* Then you run a > systemctl start file.service
* To check on the service run > systemctl status file.service
* before this can be active we have to > systyem daemon-reload
* system ctl start file.service

# SYSTEMD Tools

* systemctl reload allows for a service to be restart without effecting service performance
* systemctl enable/disable makes the service persistent through root or turns it off at login
* systemctl edit file.service --full lets you make changes to these files in post.
* systemctl list-unils --all
* systemcrl set-default lets you set a default target.

* journalctl
  - -u UNIT > helpful for dubugging issues.

### What I Did

# Lab 1

* used systemctl status file.service with su to find out the status of the device and reason for not running.
* used systemctl edit file.service --full to open the file in vim and add on a service start condition.
* added on a restart condition for anytime the device would other wise turn off. restart=always
* systemctl enable was ran so we could have the device run on root at start up.
* system daemon-reload'd so we could actively used the updated service
* sytemctl restart so that the service could start up initially as we weren't forcing a reboot.

### Important Notes

systemctl commands need to be ran as a su.
