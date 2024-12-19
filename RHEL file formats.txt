# .repo files in /etc/yum.repos.d/
----------------------------------
[repo_reponame]
name=name of the repo
baseurl=file:///path
enabled=1
gpgcheck=0

------------------------------
# user file in /etc/sudoers.d/
------------------------------
user ALL=/path/to/the/command/they/can/use, ! /path/to/the/command/they/can/use user_they_cannot_use_it_on


----------------
# Services file
----------------
[Unit]
Description=Description Of The File
After=Services that are required to be running before

[Service]
Type=ServiceEventTtype
<Type=oneshot>
ExecStart=command to be executed
User=root/otheruser
Group=specifiygroup

-----------
# Timer files
-----------
[Unit]
Description=Description Of the files

[Timer]
Event=Timer
<OnActiveSec - Defines a timer relative to the moment the timer is activated. >
<OnBootSec Defines a timer relative to when the machine was booted.>
<OnStartupSec Specifies a time relative to when the service manager was started. In most cases this is the same as OnBootSec, but not when systemd user units are used.>
<OnUnitActiveSec Defines a timer relative to when the unit that the timer activates was last activated>
<OnCalendar Defines timers based on calendar event expressions, such as daily.>
Persistent=true

[Install]
WantedBy=timers.target

----------------
# systemd-tmpfiles
----------------
mode /path mode user group age
#q /tmp 1777 root root 7d


------------
# etc/fstab
------------
/dev/partitionname /mountingpoint filesystem mountingoptions 0 0
UUID="<enteruuid>" /moutingpoint filesystem mountingoptions 0 0
LABEL=<label> /mountingpoint filesystem mountingoptions 0 0
<specifically for swap>
/dev/partitionname none swap mountingoptions 0 0
<specifically for stratis filesystems>
UUID=<UUID> /moutingpoint xfs x-systemd.requires=stratisd.service 0 0


------------------
# kickstarter.cfg
------------------
url --url="http://server"
repo --name="myrepo" --baseurl=file:///run/install/repo/AppStream
text <forces text mode installation>
vnc --password=password
clearpart -aa --drive=sda,sdb <removes all partitions>
part /home --fstype=ext4 --label=home --size=2048 --maxsize=4096 --grow <creates and mounts a partition>
network --device=ens33 --bootproto=dhcp <configures the primary network interface>
firewall --enable --service=ssh,http <opens the firewall>
timesource --ntp-server pool.ntp.org <sets up NTP>
rootpw --plaintext secret <configures plain text password>
selinux --enforcing <activates SELinux>

------------------
# automount files
------------------
# # auto.master
---------------
/destination    /etc/auto.newdir

# # auto.newdir
---------------
/destination    mode    servername:/path/to/shared
