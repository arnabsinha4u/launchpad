# Launchpad

[![Build Status](https://travis-ci.org/arnabsinha4u/launchpad.svg?branch=master)](https://travis-ci.org/arnabsinha4u/launchpad)
[![](https://images.microbadger.com/badges/image/arnabsinha4u/launchpad.svg)](https://microbadger.com/images/arnabsinha4u/launchpad)
[![](https://images.microbadger.com/badges/version/arnabsinha4u/launchpad.svg)](https://microbadger.com/images/arnabsinha4u/launchpad)

A launchpad to create training lab/workshops for DevOps tooling or any tool/technology using Ansible and Docker

![Launchpad](launchpad.jpg)

- [Launchpad](#launchpad)
  - [Slideshare Link](#slideshare-link)
  - [How To's](#how-tos)
    - [Startup](#startup)
    - [Shutdown](#shutdown)
  - [Extend Launchpad for more](#extend-launchpad-for-more)
    - [Startup specific lab](#startup-specific-lab)
    - [Shutdown specific lab](#shutdown-specific-lab)

## Slideshare Link

<https://www.slideshare.net/ArnabSinha36/ansible-docker-setting-up-your-own-workshop>

## How To's

Bootstrap host and Startup Lab (Default settings: creates 1 launchpad_lab group, lauchpad_lab1 user and one master container for the user)

```bash
./launchpad_lab.yml -t baseline,m_build_images,m_startup
```

### Startup

Startup Lab with default settings:

```bash
./launchpad_lab.yml -t users,group,m_startup
```

Scale-up Lab or Start Lab for more users (example 3 users):

```bash
./launchpad_lab.yml -t users,group,m_startup -e users=3
```

### Shutdown

Shutdown Lab with default settings:

```bash
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown
```

Scale-down of Shutdown Lab for more users (example 3 users):

```bash
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown -e users=3
```

## Extend Launchpad for more

- Create a directory as the same level of launchpadexamplehttpd
- Copy launchpad_looper.yml into the newly created directory
- Modify the Docker run section in the launchpad_looper.yml (like ports to be exposed etc.)
- Create a Dockerfile for the DevOps tooling or any tool/technology
- Startup and have fun!

### Startup specific lab

```bash
./launchpad_lab.yml -t users,group,m_build_images,m_startup -e users=2 -e lab_name=name_of_the_directory
```

### Shutdown specific lab

```bash
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown -e users=2 -e lab_name=name_of_the_directory
```
