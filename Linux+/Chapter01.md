# System Architecture
## Run levels

  - 0 Halt
  - 1: Single user mode
  - 2: Multi-user, without NFS
  - 3: Full multi-user mode
  - 4: Unused
  - 5: X11
  - 6: Reboot

    ex: `init 6` will reboot.


### /etc/systemd
Most modern systems use Systemd instead of init or Upstart.

Systemd focuses more on processes than run levels.

A "unit" is a resource that can include services, devices, and mounts.

## Psuedo Filesystems
Objects within a psuedo filesystem represent real resources and their attributes

They are dynamically generated upon boot.
 - /dev contains a files that represent hardware devices.
  ex: /dev/sda1

- /sys represents the sysfs system and contains links to devices
  ex: /sys/class/printer

Although cat-ing "files" in /proc/ will produce output, there isn't actually any data stored there.

`/run` is cleared each time you shutdown.

## Device Management
`udev` (provided by D-Bus) should recognize a hotplug device and lead the kernel module to manage it.

Sometimes you'll need to configure a device's `.rules` file.

ex (in order of execution preference):

    `/etc/udev/rules.d`
    `/run/udev/rules.d`
    `/usr/lib/udev/rules.d`

You can load an install module with `modprobe`

--
## Test Yourself
1. Pressing Ctrl+c in the GRUB menu will:
  * b. Open a command line session

2. Adding rw init=/bin/bash to your boot parameters in GRUB will:
  * a. Allow root access on booting

3. `sudo` is:
  * d. A system group whose members can access admin permissions

4. On most Linux systems, run level 1 invokes:
  * a. Single user mode

5. On Linux systems running systemd, the default run level can be found in:
  * c. /etc/systemd/system/default.target

6. You can find links to physical devices in:
  * a. /dev

7. Which is the quickest way to display details on your network device?
  * b. lspci

8. Which tools are used to watch for new plug-in devices?
  * d. udev and D-Bus

9. The correct order udev will use to read files is:
  * c. /etc/udev/rules.d, /run/udev/rules.d/, /usr/lib/udev/rules.d

10. You can load a kernel module called `lp` by using
  * a. sudo modprobe lp
