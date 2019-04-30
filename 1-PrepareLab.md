
# IBM Cloud Container Workshop
---
# Preparing the labs
---

![image-20181018184328603](images/image-20181018184328603.png)



Before you can run all the labs about containers in IBM Cloud Private, you should prepare your environment to execute those labs. Check the following instructions [Lab 0](Lab%200/README.md)


# Task 1. Install Docker Desktop on your Mac

Follow this procedure to install the latest Docker Desktop (ex Community Edition) on your Mac (**for Windows**, jump to the next session) 

Docker Desktop for Mac is favailable for free.

https://store.docker.com/editions/community/docker-ce-desktop-mac

![image-20190118113648920](images/image-20190118113648920-7807808.png)

Click on the blue button **Please Login to Download**. If you are not registred to the Docker site, then create an account. Then when you are registered and logged in, click on the **Get Docker ** button.

![image-20190118113959736](images/image-20190118113959736-7807999.png)

Double-click **Docker.dmg** to start the install process.

When the installation completes and Docker starts, the whale in the top status bar shows that Docker is running, and accessible from a terminal.

![Docker for Mac is ready](./images/install2docker.png)

Open a terminal and type :

`docker version`

You should see something similar to this screen :
```console
> docker version
Client: Docker Engine - Community
 Version:           18.09.1
 API version:       1.39
 Go version:        go1.10.6
 Git commit:        4c52b90
 Built:             Wed Jan  9 19:33:12 2019
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.1
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.6
  Git commit:       4c52b90
  Built:            Wed Jan  9 19:41:49 2019
  OS/Arch:          linux/amd64
  Experimental:     true

```
> Note that you should always have the client and the server running.

> The Docker server contains the **Docker engine**(containerd) that controls running containers. 


# Task 2. Install Docker Desktop on Windows

Follow this procedure to install the latest Docker Desktop (ex Community Edition) on Windows (for Mac, jump to the previous session) 

Docker Desktop for Windows is available for free.

https://store.docker.com/editions/community/docker-ce-desktop-windows

![image-20190118115800766](images/image-20190118115800766-7809080.png)

Click on the blue button **Please Login to Download**. If you are **not** registred to the Docker site, then create an account. Then when you are registered and logged in, click on the **Get Docker ** button.

![image-20190118114556568](images/image-20190118114556568-7808356.png)

Leave the default parameters: 

![Docker for Windows](./images/dockerwindows2.png)

After download, install Docker Desktop:

**Double-click Docker for Windows Installer** to run the installer.

> **IMPORTANT**: During the installation process, you may be informed the installer will reboot your workstation to install the virtualization feature of your PC. 


When the installation finishes, Docker starts automatically. The **whale** in the notification area indicates that Docker is running, and accessible from a terminal.

Open a command-line terminal like PowerShell, and try out some Docker commands!

Run docker version to check the version.

`docker version`

You should see something similar to this screen :
```console
> docker version
Client: Docker Engine - Community
 Version:           18.09.1
 API version:       1.39
 Go version:        go1.10.6
 Git commit:        4c52b90
 Built:             Wed Jan  9 19:33:12 2019
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          18.09.1
  API version:      1.39 (minimum version 1.12)
  Go version:       go1.10.6
  Git commit:       4c52b90
  Built:            Wed Jan  9 19:41:49 2019
  OS/Arch:          linux/amd64
  Experimental:     true
```
> Note that you should always have the client and the server running.

> The Docker server contains the **Docker engine** (containerd) that controls running containers. 

# Task 5. Install Git on your laptop

To do so : 

For MacOS :
http://mac.github.com

For Windows: 
http://git-scm.com/download/win

At some point during the installation, change to the **"Use Windows default console"** and continue the installation.
![Git for Windows](./images/git2.png)



# Task 6. Install the ibmcloud commands

The **ibmcloud** command line interface (CLI) provides a set of commands that are grouped by namespace for users to interact with IBM Cloud. In previous versions, the name of that command was "bluemix" or "bx".

You install a set of IBM Cloud commands and tools, verify the installation, and configure your environment. IBM® Cloud developer tools offer a command-line approach to creating, developing, and deploying end-to-end web, mobile, and microservice applications.

For MacOS or Linux (run as root) :
`curl -sL https://ibm.biz/idt-installer | bash`

For Windows in PowerShell (run as Administrator - your system will be rebooted at the end of installation) : 

```
Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('http://ibm.biz/idt-win-installer')
```

Results:

```console
> curl -sL https://ibm.biz/idt-installer | bash
[main] --==[ IBM Cloud Developer Tools for Linux/MacOS - Installer, v1.2.3 ]==--
[install] Starting Installation...
[install] Note: You may be prompted for your 'sudo' password during install.
[install_darwin_deps] Checking for external dependency: brew
[install_darwin_deps] Installing/updating external dependency: git
[install_darwin_deps] Installing/updating external dependency: docker
[install_darwin_deps] Installing/updating external dependency: kubectl
[install_darwin_deps] Installing/updating external dependency: helm
[install_bx] Updating existing IBM Cloud 'bx' CLI...
Checking for updates...
New version 0.13.1 is available.
Release notes: https://github.com/IBM-Cloud/bluemix-cli-release/releases/tag/v0.13.1

Do you want to update now? [Y/n]> 
FAILED
Could not read from input: EOF

[install_bx] Running 'bx --version'...
bx version 0.12.1+a6d7092-2018-11-19T10:31:10+00:00
[install_plugins] Installing/updating IBM Cloud CLI plugins used by IDT...
[install_plugins] Checking status of plugin: cloud-functions
[install_plugins] Installing plugin 'cloud-functions'
Looking up 'cloud-functions' from repository 'IBM Cloud'...
Plug-in 'cloud-functions 1.0.27' found in repository 'IBM Cloud'
Attempting to download the binary file...
 11.55 MiB / 11.55 MiB [=============================================================================================================] 100.00% 4s
12110032 bytes downloaded
Installing binary...
OK
Plug-in 'cloud-functions 1.0.27' was successfully installed into /Users/phil/.bluemix/plugins/cloud-functions. Use 'bx plugin show cloud-functions' to show its details.
[install_plugins] Checking status of plugin: container-registry
[install_plugins] Updating plugin 'container-registry' from version '0.1.347'
Plug-in 'container-registry 0.1.347' was installed.
Checking upgrades for plug-in 'container-registry' from repository 'IBM Cloud'...
No updates are available.
[install_plugins] Checking status of plugin: container-service
[install_plugins] Installing plugin 'container-service'
Looking up 'container-service' from repository 'IBM Cloud'...
Plug-in 'container-service/kubernetes-service 0.2.19' found in repository 'IBM Cloud'
Attempting to download the binary file...
 22.77 MiB / 22.77 MiB [=============================================================================================================] 100.00% 8s
23876968 bytes downloaded
Installing binary...
OK
Plug-in 'container-service 0.2.19' was successfully installed into /Users/phil/.bluemix/plugins/container-service. Use 'bx plugin show container-service' to show its details.
[install_plugins] Checking status of plugin: dev
[install_plugins] Updating plugin 'dev' from version '2.1.12'
Plug-in 'dev 2.1.12' was installed.
Checking upgrades for plug-in 'dev' from repository 'IBM Cloud'...
No updates are available.
[install_plugins] Checking status of plugin: sdk-gen
[install_plugins] Updating plugin 'sdk-gen' from version '0.1.12'
Plug-in 'sdk-gen 0.1.12' was installed.
Checking upgrades for plug-in 'sdk-gen' from repository 'IBM Cloud'...
No updates are available.
[install_plugins] Running 'bx plugin list'...
Listing installed plug-ins...

Plugin Name                            Version   Status   
container-service/kubernetes-service   0.2.19       
dev                                    2.1.12       
icp                                    2.1.284      
schematics                             1.2.0        
sdk-gen                                0.1.12       
cloud-functions/wsk/functions/fn       1.0.27       
container-registry                     0.1.347 

[install_plugins] Finished installing/updating plugins
[install] Install finished.
[main] --==[ Total time: 46 seconds ]==--

```

To verify that the CLI and developer tools were installed successfully, run the help command:

`ibmcloud dev help`

Results:

```console
ibmcloud dev help
NAME:
   ibmcloud dev - A CLI plugin to create, manage, and run applications on IBM Cloud

USAGE:
   ibmcloud dev command [arguments...] [command options]

VERSION:
   2.1.4

COMMANDS:
   build             Build the application in a local container
   code              Download the code from an application
   console           Opens the IBM Cloud console for an application
   create            Creates a new application and gives you the option to add services
   diag              This command displays version information about installed dependencies
   debug             Debug your application in a local container
   delete            Deletes an application from your space
   deploy            Deploy an application to IBM Cloud
   edit              Add or remove services for your application
   enable            Add IBM Cloud files to an existing application.
   get-credentials   Gets credentials required by the application to enable use of connected services.
   list              List all IBM Cloud applications in a space
   run               Run your application in a local container
   shell             Open a shell into a local container
   status            Check the status of the containers used by the CLI
   stop              Stop a container
   test              Test your application in a local container
   view              View the URL of your application
   help              Show help
   
Enter 'ibmcloud dev help [command]' for more information about a command.

GLOBAL OPTIONS:
   --version, -v                  Print the version
   --help, -h                     Show help

```

You can also verify your CLI installation by typing:

`ibmcloud plugin list` 

Results:

```console
ibmcloud plugin list
Listing installed plug-ins...

Plugin Name                            Version   
container-registry                     0.1.339   
container-service/kubernetes-service   0.1.581   
...
```




---
# End of the lab
---
# IBM Cloud Container Workshop
---
