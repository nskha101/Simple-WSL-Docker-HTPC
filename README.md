# HTPC Download Box for WSL

Sonarr / Radarr / Prowlarr / NZBGet / Overseerr / Unmanic / Immich

My personal HTPC/HomeLab setup, with a simple docker setup. This version has been tailored to run on Windows with WSL2 using a Ubuntu Distro, and accounts for the restrictions associated with that.

Special thanks to (https://github.com/sebgl/htpc-download-box) for the inspiration, this setup is based on his fantastic work.

## Background

We use Sonarr/Radarr to grab content, NZBGet to download it, Prowlarr to manage our usenet indexers, Overseerr to make user-friendly requests, Unmanic to optimize our library, and Immich as a seperate service to provide image backup. 

Immich and Unmanic are hardware accelerated using a Nvidia GPU (3070, in my case). Please see (https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html) for installation instructions prior to running this. If you don't want to use HW ACC, skip this and comment out the related sections of the compose file. 

Dockerized plex isn't included as part of this as I intend to run that seperately installed directly on windows, however it can easily be added by checking out the setup here: (https://github.com/sebgl/htpc-download-box)

I use this in conjunction with [Stablebit Drivepool](https://stablebit.com/) to organize my hodge-podge of drives to one large, mountable windows drive. That's accessible in WSL using the `/mnt` directory, thus we mount that to the HTPC container so that they can store data on there. We do the same with Immich and Unmanic to give access to the stablebit virtual drive. You don't need to do this, however it makes things trivial to setup. 

## Installation

1. Install docker and setup WSL2 with ubuntu. Here's a good guide: (https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10#1-overview) 
2. OPTIONAL - Install Nvidia container toolkit for hardware acceleration: (https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)
3. Clone this git repo
4. Rename `.env.example` to `.env`, and fill out the required fields. 
5. Run `docker compose up -d` and ensure everything is working
6. Confirm everything is working by visiting available services, and proceed with setup, I'd reccomend reading through (https://github.com/sebgl/htpc-download-box) for each service to get specific setup instructions
7. OPTIONAL - Port forward addresses to access them from outside your LAN

Done! 

## Coming up next...

- Plex-meta-manager
- Reverse proxy
- ???