# Launchpad
A launchpad to create training lab/workshops for DevOps tooling or any tool/technology using Ansible and Docker

### How To's:
Bootstrap host and Startup Lab (Default settings: creates 1 launchpad_lab group, lauchpad_lab1 user and one master container for the user)
```
./launchpad_lab.yml -t baseline,m_build_images,m_startup
```

#### Startup
Startup Lab with default settings:
```
./launchpad_lab.yml -t users,group,m_startup
```

Scale-up Lab or Start Lab for more users (example 3 users):
```
./launchpad_lab.yml -t users,group,m_startup -e users=3
```

#### Shutdown
Shutdown Lab with default settings:
```
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown
```

Scale-down of Shutdown Lab for more users (example 3 users):
```
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown -e users=3
```

### Extend Launchpad for more!
* Create a directory as the same level of launchpad_example_httpd
* Copy launchpad_looper.yml into the newly created directory
* Create a Dockerfile for the DevOps tooling or any tool/technology
* Startup and have fun!
#### Startup
```
./launchpad_lab.yml -t users,group,m_build_images,m_startup -e users=2 -e lab_name=name_of_the_directory
```
#### Shutdown
```
./launchpad_lab.yml -t remove_group,remove_users,m_shutdown -e users=2 -e lab_name=name_of_the_directory
```
