## CLI Commands
The following is a list of CLI commands that you must be familiar with for the RHCSA 9 examination. These commands were based on the video and textual course from Sander Van Vugt.

## Set Password with Echo Command

- `echo password | passwd --stdin user`: This command allows you to set the password of a user without using the interactive prompt.

## Word Count Command

- `wc -l`: Counts the number of lines in a file.

## Man and Search Commands

- `man -k searchterm`: This command gives a list of possible matches in the manual along with the section that the information is in. Equivalent to `apropos`.

## Find Command

- `find /path -name filename -type f/d -exec command {}\;`: This is a `find` command with the `-exec` option that triggers a command. The `{}` are placeholders for the filenames resulting from the search.

## Tar Commands

- `tar cvf /archive.tar /targetstoarchive`: Compresses files.
- `tar xvf /archive.tar /extraction/path`: Extracts files from the archive.
- `tar tvf /archive.tar`: Views the contents of the archive.
- `tar rvf /archive.tar /newfiles`: Appends new files to a preexisting archive.
- `tar cvfz /archive.gz /targetstoarchive`: Compresses using gzip compression.
- `tar cvfJ /archive.xz /targetstoarchive`: Compresses using xz compression.
- `tar cvfj /archive.bz2 /targetstoarchive`: Compresses using bzip2 compression.

## Awk Command

- `awk -F : '{command}' file`: The `-F` specifies the field separator. For example, `awk -F : '{print $1, $3}' file.txt` prints the first and third columns in file.txt. The `:` is used as a field separator. Without specifying a field separator, it will use a space by default.

## Sed Commands

- `sed -i s/searchterm/replacement/g file`: Replaces a specific term in a file. The `-i` writes changes to the file immediately, and `g` applies the change to all instances of the search term.
- `sed -i '10d' file`: Deletes the 10th line in a file.

## User and Group Commands

- `useradd <username> -s /sbin/nologin`: Adds a user to the system. The `-s` sets the login shell to `/sbin/nologin`, preventing login.
- `usermod -aG groupname user`: Adds the user to the `groupname` as a secondary group. The `-a` appends rather than replacing secondary groups.
- `usermod -L user`: Locks the user account.
- `usermod -U user`: Unlocks the user account.
- `usermod -e <date> user`: Sets the account expiration date for the user.
- `passwd -l user`: Locks the user’s password.
- `passwd -u user`: Unlocks the user’s password.
- `usermod -s /sbin/nologin user`: Changes the user’s login shell to `/sbin/nologin`, preventing login.
- `lid -g groupname`: Lists all members of a group.

## Chage Command

- `chage user`: Changes user password properties, such as the minimum and maximum time before a password change, and password expiration.

## Chmod Commands

- `chmod g+s .`: Applies `setgid` permission on a directory, allowing new files created in the directory to inherit group ownership.
- `chmod +t .`: Applies a sticky bit to a file or directory.

## Hostname Command

- `hostnamectl set-hostname <hostname>`: Changes the system’s hostname. Can also be changed by editing `/etc/hostname` or through the `nmtui` command.

## Nmcli Commands

- `nmcli`: Opens the NetworkManager command-line interface.
- `nmcli connection up <connectionname>`: Re-establishes the specified connection.

## Ss Commands

- `ss -tu`: Shows TCP packets.
- `ss -tuna`: Shows both TCP and UDP packets.
- `ss -tunap`: Shows all sockets without resolving service names, including processes using the sockets.

## Rpm Commands

- `rpm -qa`: Lists all installed packages.
- `rpm -qf filename`: Displays which package installed the specified file.
- `rpm -ql packagename`: Lists all files from the specified package.
- `rpm -q --scripts packagename`: Shows the scripts executed during the installation of the specified package.
- `rpm -q --changelog packagename`: Shows the changelog for the specified package.

## Rpm2cpio Commands

- `rpm2cpio packagename.rpm | cpio -idmv`: Converts the RPM package to a CPIO data stream, listing files while extracting them to the current directory.
- `rpm2cpio packagename.rpm | cpio -tv`: Lists the contents of a package without extracting it.

## Dnf Commands

- `dnf config-manager --enable reponame`: Enables a specific repository.
- `dnf config-manager --add-repo=file:///path/to/repo`: Adds a third-party repository.
- `dnf list`: Lists all installed packages.
- `dnf list searchterm`: Lists all packages matching the search term.
- `dnf search`: Searches package names and metadata.
- `dnf search all`: Searches names and descriptions.
- `dnf provides */searchterm`: Searches for the package containing the specified file.
- `dnf info`: Displays information about the specified package.
- `dnf install packagename`: Installs the specified package.
- `dnf remove packagename`: Removes the specified package.
- `dnf update`: Updates all installed packages.
- `dnf repoquery`: Queries information from enabled repositories.
- `dnf download`: Downloads the specified package.
- `dnf history`: Displays a history of DNF transactions.
- `dnf history undo x`: Reverses a specified transaction.

## Lscpu Command

- `lscpu`: Displays CPU architecture information.

## Uptime Command

- `uptime`: Displays system uptime and load average.

## Nice and Renice Commands

- `nice -n <priority> -p <PID>`: Sets the priority of a process.
- `renice -n <priority> -p <PID>`: Changes the priority of a process.

## Kill Command

- `kill -SIGCHLD <pid>`: Sends a signal to the parent process to remove a zombie process.

## Tuned-adm Commands

- `tuned-adm list`: Lists all available tuned profiles.
- `tuned-adm profile <profilename>`: Applies the specified tuned profile.

## Loginctl Commands

- `loginctl list-users`: Lists all active users.
- `loginctl list-sessions`: Lists all active sessions with associated users.
- `loginctl terminate-session <id>`: Terminates a specific session.
- `loginctl terminate-user <user>`: Terminates all sessions of a specific user.
- `loginctl user-status <username>`: Displays the status of the specified user.

## Systemctl Commands

- `systemctl list-units`: Lists all active units that `systemd` knows about.
- `systemctl list-unit-files`: Lists all installed unit files.
- `systemctl list-unit -t timer`: Lists all units of type "timer."
- `systemctl status <servicename>`: Displays the status of the specified service.
- `systemctl start <servicename>`: Starts the specified service.
- `systemctl stop <servicename>`: Stops the specified service.
- `systemctl enable <servicename>`: Enables the specified service to start at boot.
- `systemctl disable <servicename>`: Disables the specified service from starting at boot.
- `systemctl reload <servicename>`: Reloads the specified service’s configuration.
- `systemctl restart systemd-journald-flush`: Reloads the new `systemd-journal` parameters.
- `systemctl unit-dependencies <servicename>`: Lists all dependencies of a specific service.
- `systemctl isolate <target>`: Switches to the specified target.
- `systemctl get-default`: Displays the current default target.
- `systemctl set-default <target>`: Sets the default target.
- `systemctl enable --now debug-shell.service`: Enables and starts the debug shell, available with `Ctrl + Alt + F9`.

## Journalctl Commands

- `journalctl`: Displays the systemd journal.
- `journalctl -u <servicename>`: Displays the logs for a specific service.
- `journalctl -p err`: Displays only logs with a priority of error.
- `journalctl -b`: Displays the boot log.
- `journalctl -xb`: Displays boot log with explanations.

## Timedatectl Commands

- `timedatectl`: Prints system time and date information.
- `timedatectl status`: Shows the current system time, date, and time zone.
- `timedatectl set-time <time>`: Sets the system clock.
- `timedatectl set-timezone <timezone>`: Sets the system timezone.
- `timedatectl set-ntp <boolean>`: Enables or disables network time synchronization.

## Disk Management Commands

- `lsblk`: Lists all block devices.
- `lsblk -f`: Lists block devices and their filesystems.
- `fdisk -l`: Lists disk partitions.
- `fdisk /dev/<device>`: Opens the disk for partitioning using `fdisk`.

## Filesystem Commands

- `mkfs.<filesystem> /dev/<partition>`: Creates a filesystem on the specified partition.
- `mount /dev/<partition> /mnt`: Mounts the specified partition at `/mnt`.
- `mount -a`: Mounts all filesystems defined in `/etc/fstab`.
- `blkid`: Displays UUID and label information of all block devices.
- `findmnt --verify`: Verifies `/etc/fstab` syntax.

## Fdisk Commands

- `fdisk devicename`: Opens the disk management utility.
  - `m`: Opens help in `fdisk`.
  - `n`: Creates a new partition.
  - `p`: Prints partition information.
  - `w`: Writes changes to the disk.
  - `t`: Sets the partition type.

  ## Tune2fs Command

- `tune2fs -L <label> /device`: Sets the label on a device with an ext filesystem.

## Xfs_admin Command

- `xfs_admin -L <label> /device`: Sets the label on an XFS filesystem.

## Gdisk Commands

- `gdisk`: Opens the GPT disk management utility.
  - `?`: Opens help in `gdisk`.
  - `n`: Creates a new GPT partition.

## Swapoff Command

- `swapoff /dev/partition`: Disables the swap on the specified partition.

## Swap Management Commands

- `mkswap /dev/<partition>`: Sets up the specified partition as swap space.
- `swapon /dev/<partition>`: Enables the specified swap partition.

## LVM Commands

- `pvcreate /dev/<partition>`: Initializes the partition as a physical volume for LVM.
- `vgcreate <groupname> /dev/<partition>`: Creates a volume group with the specified partition.
- `lvcreate -L <size> -n <lvname> <groupname>`: Creates a logical volume in the specified volume group.
- `lvresize -L +<size> /dev/<vgname>/<lvname>`: Resizes a logical volume.
- `vgextend <vgname> /dev/<partition>`: Extends the volume group by adding a new partition.
- `vgreduce <vgname> /dev/<partition>`: Removes a partition from the volume group.
- `lvextend -L +<size> /dev/<vgname>/<lvname>`: Extends the size of the logical volume.
- `lvreduce -L -<size> /dev/<vgname>/<lvname>`: Reduces the size of the logical volume.
- `pvmove /dev/<source> /dev/<target>`: Moves data from one partition to another.

## Grub Commands

- `grub2-mkconfig -o /boot/grub2/grub.cfg`: Generates the GRUB2 configuration file.

## SELinux Commands

- `getenforce`: Displays the current SELinux mode.
- `setenforce <mode>`: Sets the SELinux mode to `enforcing` or `permissive`.
- `semanage fcontext -a -t <context> <file>`: Adds a context rule for the specified file.
- `restorecon -Rv <directory>`: Restores SELinux context on a directory recursively.
- `semanage port -l`: Lists port context rules.
- `setsebool -P <boolean> on/off`: Enables or disables a specific SELinux boolean value persistently.

## Firewall-cmd Commands

- `firewall-cmd --list-all`: Lists all active firewall settings.
- `firewall-cmd --get-services`: Lists all predefined services.
- `firewall-cmd --add-service <service> --permanent`: Adds the specified service to the active firewall rules.

## Podman Commands

- `podman run <options> <image> <command>`: Runs a container from an image with specified options.
- `podman ps`: Lists running containers.
- `podman ps -a`: Lists all containers, including stopped ones.
- `podman stop <container>`: Stops the specified container.
- `podman rm <container>`: Removes the specified container.
- `podman pull <image>`: Pulls the specified image from the registry.
- `podman exec <container> <command>`: Executes a command in a running container.
- `podman logs <container>`: Displays logs of the specified container.
- `podman images`: Lists all images stored locally.
- `skopeo inspect docker://<image>`: Inspects a container image without downloading it.
- `podman unshare`: Runs a command in a new user namespace.
  - `chown nn:nn directoryname`: Changes ownership of a directory in the namespace.
  - `generate systemd --now <container> --files --new`: Generates systemd unit files for the container.
