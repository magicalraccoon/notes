# Linux Installation and Package Management
## Disk Partitioning
- `df -h` will list free disk usage
- `du -sh` will list the space files or directories take


- **LVM** = Logical Volume Manager
- **PV** = Physical Volume
- **VG** = Volume Group
- **LV** = Logical Volume

`vgcreate` will create a new volume group.

`lvcreate` will add it to part of a logical volume.

`lvscan` will scan for all logical volumes.


## Install and Configure a Boot Manager
You can install GRUB on additional drives, but you must configure it with `grub-mkconfig` or `grub2-mkconfig`.

## Shared Libraries
Libraries allow software to interact with the local environment.

#### Static and Dynamic libraries
  - **Static** = gathered into a program at installation time
  - **Dynamic** = accessed whenever a program needs it

ex: `libip6tc.so.0.1.0`
  - lib - library
  - ip6tc - package name
  - so - shared object (dynamic library)
    - (static library would be "a")
  - 0.1.0 - version number

You can use `ldd` to display the libraries that a package depends on.

`ldconfig -p` will list all the libraries in the current cache.

Library data is stored in `/etc/ld.so.cache`, and gets information through links in `/etc/ld.so.conf`

--
## Package Managers
### Debian / Ubuntu -
**Local**: `dpkg`
  - Configured through `etc/dpkg/dpkg.cfg`.
  - to directly install a package, use:
    `sudo dpkg -i my_package_2.4.1-1_amd64.deb`.
  - You can also unpack without installing by using the `--unpack` flag.
  - Packages can also be Removed (`r`), Purged (`-P`), and Reconfigured (`dpkg-reconfigure`).
  - List all currently installed packages with the `-l` flag.
**Repositories**: `APT`
  - you know how to do this.

### Fedora / CentOS / RHEL
**Local**: `RPM`
  - Similar to APT.
  - Install a package with `rpm -i software.rpm`.
  - Verify the integrity with the `-V` flag.
  - Return a file's checksum with the `-vK` flag.
  - You can also use `rpm -i --test` to check for dependencies.
**Repositories**: `yum`
  - Preferences are configured in `/etc/yum/repos.d/` and `/etc/yum.conf`.
  - Packages can be downloaded without installing with `yumdownloader --resolve packagename`. `--resolve` adds dependencies.
  - `yum search` and `yum info` will display detailed information.
  - .rpm files are stored as a compressed `cpio` archive.

--
## Test Yourself
1. Which of these is NOT commonly given its own partition?
  b. /etc

2. The primary goal of LVM is to allow you to ...
  d. Provide easy access to resources on distributed partitions
    - Files can be upgraded with `-U`.
    - The `-q` flag will display the currently installed version.
    - Remove a package with the `-e` flag.
    - To list all currently installed packages, use `rpm -q -a`.
    - For detailed information about a package, use `-qid`.

  % Repositories: yum
    - Preferences are configured in `/etc/yum/repos.d/` and `/etc/yum.conf`.
    - Packages can be downloaded without installing with `yumdownloader --resolve packagename`. `--resolve` adds dependencies.
    - `yum search` and `yum info` will display detailed information.
    - .rpm files are stored as a compressed `cpio` archive.

1. Which of these is NOT commonly given its own partition?
  * b. /etc

2. The primary goal of LVM is to allow you to ...
  * d. Provide easy access to resources on distributed partitions

3. Changes to GRUB settings will not take effect until you run...
  * a. grub-mkconfigX d. Run ldconfig -u

4. Which of these is incorporated into program code during installation?
  * c. Static libraries

5. Which of these will list all libraries currently stored in cache?
  * c. ldconfig -p

6. When you create your own library, you need to ...
  * b. Add a file pointing to its location to the /etc/ld.so.conf.d directory

7. ____ manages online repo-based software for Red Hat Linux:
  * a. YUM

8. You can install VLC on a Debian system using:
  * a. apt-get install vlc

9. You can delete VLC from a Debian system using:
  * d. apt-get remove VLC

10. YUM repository settings are defined by:
  * d. /etc/yum.repos.d
