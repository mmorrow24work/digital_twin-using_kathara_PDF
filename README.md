# Insatll Docker
```
mmorrow24work@digital-twin-version-1-0:~/docker/custom-images/docker_custom_image_kathara_zabbix7.4_frr$ sudo apt install docker
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 wmdocker
The following NEW packages will be installed:
  docker libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 wmdocker
0 upgraded, 7 newly installed, 0 to remove and 4 not upgraded.
Need to get 1257 kB of archives.
After this operation, 3673 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 file:/etc/apt/mirrors/debian.list Mirrorlist [30 B]
Get:2 https://deb.debian.org/debian bookworm/main amd64 libxau6 amd64 1:1.0.9-1 [19.7 kB]
Get:3 https://deb.debian.org/debian bookworm/main amd64 libxdmcp6 amd64 1:1.1.2-3 [26.3 kB]
Get:4 https://deb.debian.org/debian bookworm/main amd64 libxcb1 amd64 1.15-1 [144 kB]
Get:5 https://deb.debian.org/debian bookworm/main amd64 libx11-data all 2:1.8.4-2+deb12u2 [292 kB]
Get:6 https://deb.debian.org/debian bookworm/main amd64 libx11-6 amd64 2:1.8.4-2+deb12u2 [760 kB]
Get:7 https://deb.debian.org/debian bookworm/main amd64 wmdocker amd64 1.5-2 [12.8 kB]
Get:8 https://deb.debian.org/debian bookworm/main amd64 docker all 1.5-2 [2556 B]
Fetched 1257 kB in 0s (6905 kB/s)
Selecting previously unselected package libxau6:amd64.
(Reading database ... 75624 files and directories currently installed.)
Preparing to unpack .../0-libxau6_1%3a1.0.9-1_amd64.deb ...
Unpacking libxau6:amd64 (1:1.0.9-1) ...
Selecting previously unselected package libxdmcp6:amd64.
Preparing to unpack .../1-libxdmcp6_1%3a1.1.2-3_amd64.deb ...
Unpacking libxdmcp6:amd64 (1:1.1.2-3) ...
Selecting previously unselected package libxcb1:amd64.
Preparing to unpack .../2-libxcb1_1.15-1_amd64.deb ...
Unpacking libxcb1:amd64 (1.15-1) ...
Selecting previously unselected package libx11-data.
Preparing to unpack .../3-libx11-data_2%3a1.8.4-2+deb12u2_all.deb ...
Unpacking libx11-data (2:1.8.4-2+deb12u2) ...
Selecting previously unselected package libx11-6:amd64.
Preparing to unpack .../4-libx11-6_2%3a1.8.4-2+deb12u2_amd64.deb ...
Unpacking libx11-6:amd64 (2:1.8.4-2+deb12u2) ...
Selecting previously unselected package wmdocker.
Preparing to unpack .../5-wmdocker_1.5-2_amd64.deb ...
Unpacking wmdocker (1.5-2) ...
Selecting previously unselected package docker.
Preparing to unpack .../6-docker_1.5-2_all.deb ...
Unpacking docker (1.5-2) ...
Setting up libxau6:amd64 (1:1.0.9-1) ...
Setting up libxdmcp6:amd64 (1:1.1.2-3) ...
Setting up libxcb1:amd64 (1.15-1) ...
Setting up libx11-data (2:1.8.4-2+deb12u2) ...
Setting up libx11-6:amd64 (2:1.8.4-2+deb12u2) ...
Setting up wmdocker (1.5-2) ...
Setting up docker (1.5-2) ...
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for libc-bin (2.36-9+deb12u10) ...
mmorrow24work@digital-twin-version-1-0:~/docker/custom-images/docker_custom_image_kathara_zabbix7.4_frr$

```

The error you got means the default `docker` package you installed is not the Docker Engine service, and hence the `docker` command and `docker.service` were not found.

On Debian 12 Bookworm, the **proper way to install Docker Engine** is to install packages from Docker's official repository, not the default Debian `docker` package.

***

## How to properly install Docker Engine on Debian 12 Bookworm

1. **Update system and install dependencies**

```bash
sudo apt update
sudo apt install ca-certificates curl gnupg lsb-release
```

2. **Add Docker’s official GPG key**

```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. **Add the Docker repository**

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

4. **Update and install Docker Engine packages**

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

5. **Start and enable Docker service**

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

6. **Verify Docker is running**

```bash
sudo systemctl status docker
docker --version
```

***

After this, you should have the official Docker Engine installed, with the `docker` command available and the service running.

***

If you want, I can guide you step-by-step through this installation process!

[1] https://xtom.com/blog/how-to-install-docker-and-docker-compose-on-debian-12-bookworm/
[2] https://greenwebpage.com/community/how-to-install-docker-on-debian-12/
[3] https://linuxiac.com/how-to-install-docker-on-debian-12-bookworm/
[4] https://www.ionos.co.uk/digitalguide/server/configuration/install-docker-on-debian-12/
[5] https://docs.docker.com/engine/install/debian/
[6] https://www.thomas-krenn.com/en/wiki/Docker_installation_on_Debian_12
[7] https://docs.vultr.com/how-to-install-docker-on-debian-12
[8] https://docs.docker.com/desktop/setup/install/linux/debian/
[9] https://reintech.io/blog/setting-up-docker-docker-compose-debian-12
[10] https://www.reddit.com/r/debian/comments/uz22e6/dockerce_on_debian_12_wormbook/


# Insatll Kathara
```
mmorrow24work@digital-twin-version-1-0:~/kathara$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 21805A48E6CBBA6B991ABE76646193862B759810
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
Executing: /tmp/apt-key-gpghome.iCjrxUx15D/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 21805A48E6CBBA6B991ABE76646193862B759810
gpg: key 646193862B759810: public key "Launchpad PPA for Kathara Framework" imported
gpg: Total number processed: 1
gpg:               imported: 1
mmorrow24work@digital-twin-version-1-0:~/kathara$ date
Tue Aug 26 11:44:01 UTC 2025
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ echo "deb [ signed-by=/usr/share/keyrings/ppa-kathara-archive-keyring.gpg ] http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/kathara.list
echo "deb-src [ signed-by=/usr/share/keyrings/ppa-kathara-archive-keyring.gpg ] http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy main" | sudo tee -a /etc/apt/sources.list.d/kathara.list
deb [ signed-by=/usr/share/keyrings/ppa-kathara-archive-keyring.gpg ] http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy main
deb-src [ signed-by=/usr/share/keyrings/ppa-kathara-archive-keyring.gpg ] http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy main
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ wget -qO - "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x21805a48e6cbba6b991abe76646193862b759810" | sudo gpg --dearmor -o /usr/share/keyrings/ppa-kathara-archive-keyring.gpg
mmorrow24work@digital-twin-version-1-0:~/kathara$ 
mmorrow24work@digital-twin-version-1-0:~/kathara$ sudo apt update
Get:1 file:/etc/apt/mirrors/debian.list Mirrorlist [30 B]
Get:5 file:/etc/apt/mirrors/debian-security.list Mirrorlist [39 B]                                                                        
Get:7 http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy InRelease [18.1 kB]
Hit:8 https://packages.cloud.google.com/apt google-compute-engine-bookworm-stable InRelease       
Hit:2 https://deb.debian.org/debian bookworm InRelease                                            
Hit:3 https://deb.debian.org/debian bookworm-updates InRelease
Hit:4 https://deb.debian.org/debian bookworm-backports InRelease
Hit:6 https://deb.debian.org/debian-security bookworm-security InRelease
Hit:9 https://packages.cloud.google.com/apt cloud-sdk-bookworm InRelease
Hit:10 https://packages.cloud.google.com/apt google-cloud-ops-agent-bookworm-2 InRelease
Get:11 http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy/main Sources [796 B]
Get:12 http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy/main amd64 Packages [544 B]
Get:13 http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy/main Translation-en [292 B]
Fetched 19.7 kB in 1s (14.8 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
mmorrow24work@digital-twin-version-1-0:~/kathara$ sudo apt install kathara
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  docker.io | docker-ce xterm
The following NEW packages will be installed:
  kathara
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 30.0 MB of archives.
After this operation, 160 MB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/katharaframework/kathara/ubuntu jammy/main amd64 kathara amd64 3.8.0-1jammy [30.0 MB]
Fetched 30.0 MB in 1s (32.5 MB/s)  
Selecting previously unselected package kathara.
(Reading database ... 75552 files and directories currently installed.)
Preparing to unpack .../kathara_3.8.0-1jammy_amd64.deb ...
Unpacking kathara (3.8.0-1jammy) ...
Setting up kathara (3.8.0-1jammy) ...
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for libc-bin (2.36-9+deb12u10) ...
mmorrow24work@digital-twin-version-1-0:~/kathara$
```
