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
