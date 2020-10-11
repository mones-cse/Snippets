# After Ubuntu Setup


## Install snapd
**Snapd** is a tool that will help us to install the latest software easily.

```console 
$ sudo apt update
$ sudo apt install snapd
```


## Install the software using snpad
most of the commands are self-explanatory 

```console
$ sudo snap install pycharm-professional --classic
$ sudo snap install webstorm --classic
$ sudo snap install datagrip --classic
$ sudo snap install code --classic
$ sudo snap install postman

$ sudo snap install slack --classic

$ sudo snap install vlc
$ sudo snap install chromium
```

## Install git
```console
$ sudo apt-get install git
```
### Config git in local using 
```git
git config --global user.email "mones.cse@gmail.com"
git config --global user.name "mones"
```
### Git and SSH
1. [Generating a new SSH key](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
2. [Adding your SSH key to the ssh-agent](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)
3. [Adding a new SSH key to your GitHub account](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)


## Handle sound issue 
By default, Ubuntu does not have any support for both headphone and speaker selection facility.
By default, we need to unplug the headphone each time we want to use speaker.
To avoid that situation, we need to do a couple of things

1. As we are using one sound drive and multiple ports to play speaker and headphone we need to use [sound switch indicator](https://yktoo.com/en/software/sound-switcher-indicator/) and from it's the preference we can add **lineout** as a speaker and **headphone** as a headphone
2. Install **alsamixer** using the following command 
   ```
   sudo apt update
   sudo apt install alsa-utils
   ```
3. run **alsamixer ** from command line and understand details status
4. read full answer from [here](https://askubuntu.com/questions/829520/ubuntu-16-04-no-sound-from-speakers-only-headphones-working/929766#929766) and follow the steps to change `analog-output-headphones.conf` file with following code 
 ```bash
  [Element Front]
  switch = off
  volume = zero
```


## install terminator
[Terminator](https://terminator-gtk3.readthedocs.io/en/latest/) is a terminal emulator. Install it using  
```
$ sudo apt-get install terminator
``` 
Setting terminator for default terminal
```
$ sudo update-alternatives --config x-terminal-emulator
```
Change the following file to create a custom structure
```
nano ~/.config/terminator/config 
```
 with following code
```yml
[global_config]
[keybindings]
[layouts]
  [[default]]
    [[[child0]]]
      fullscreen = False
      last_active_term = 14f98214-6f01-4fb8-9d13-265a756ef2e8
      last_active_window = True
      maximised = True
      order = 0
      parent = ""
      position = 67:27
      size = 1533, 845
      title = mones@mones-pc: ~
      type = Window
    [[[child1]]]
      order = 0
      parent = child0
      position = 763
      ratio = 0.499345549738
      type = HPaned
    [[[child3]]]
      order = 1
      parent = child1
      position = 422
      ratio = 0.502380952381
      type = VPaned
    [[[terminal2]]]
      order = 0
      parent = child1
      profile = mones
      type = Terminal
      uuid = aa55379e-5996-44c8-aedf-a37722e2a7cf
    [[[terminal4]]]
      order = 0
      parent = child3
      profile = default
      type = Terminal
      uuid = 14f98214-6f01-4fb8-9d13-265a756ef2e8
```
If we want to change this layout create a new layout and save it after that copy that new custom code and replace it with default content.

## install nvm
```console
$ apt-get update -y
$ apt-get install build-essential libssl-dev -y
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
$ source ~/.profile
$ nvm --version
```

## install pyenv
pyenv lets you easily switch between multiple versions of Python. Before install pyenv we need to install some [prerequisite](https://github.com/pyenv/pyenv/wiki/Common-build-problems) which are given bellow 

```
sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
```
after that we are going to install pyenv using [pyenv installer](https://github.com/pyenv/pyenv-installer) using following line of command

```
$ curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```
after that we need to update `.bashrc` file we can access that using `nano ~/.bashrc` command and inside the file, add following command at the bottom .

```console
# Load pyenv automatically by adding
# the following to ~/.bashrc:

export PATH="/home/mones/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
after that to check the effect restart the console using `$ exec $SHELL` command.

## install virtualenv
[virtualenv](https://virtualenv.pypa.io/en/latest/) is a tool to create isolated Python environments. To install this use following command 
```
sudo apt install virtualenv
```


## Update Visual Code studio watch limit 
 Some time VS Code file watcher is running out of handles because the workspace is large. we can solve this problem using this [guide](https://code.visualstudio.com/docs/setup/linux#_visual-studio-code-is-unable-to-watch-for-file-changes-in-this-large-workspace-error-enospc)


## Ngrok 
**ngrok** is a cross-platform application that enables developers to expose a local development server to the Internet with minimal effort. The software makes your locally-hosted web server appear to be hosted on a subdomain of ngrok.com, meaning that no public IP or domain name on the local machine is needed.

For installation just follow their [guideline](https://dashboard.ngrok.com/get-started/setup).


## Docker
follow this [link](https://medium.com/devgorilla/how-to-install-docker-on-ubuntu-18-04-495216a16092) to install docker however if `Executing the Docker Command Without Sudo` does not work check [this](https://docs.docker.com/engine/install/linux-postinstall/) and if we got issues like `Got permission denied while trying to connect to the Docker daemon socket` follow this [instruction](https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket) command like `$ sudo chmod 666 /var/run/docker.sock` solve the problem


## redshift
install redshift ` $ sudo apt-get install redshift`

install redshift-gtk for gui ` $ sudo apt install redshift-gtk` 

add config for manual location in `nano ~/.config/redshift.conf` and add following code there


```
; Global settings for redshift
[redshift]
; Set the day and night screen temperatures
temp-day=5700
temp-night=3500

; Enable/Disable a smooth transition between day and night
; 0 will cause a direct change from day to night screen temperature.
; 1 will gradually increase or decrease the screen temperature.
transition=1

; Set the screen brightness. Default is 1.0.
;brightness=0.9
; It is also possible to use different settings for day and night
; since version 1.8.
;brightness-day=0.7
;brightness-night=0.4
; Set the screen gamma (for all colors, or each color channel
; individually)
gamma=0.8
;gamma=0.8:0.7:0.8
; This can also be set individually for day and night since
; version 1.10.
;gamma-day=0.8:0.7:0.8
;gamma-night=0.6

; Set the location-provider: 'geoclue', 'geoclue2', 'manual'
; type 'redshift -l list' to see possible values.
; The location provider settings are in a different section.
location-provider=manual

; Set the adjustment-method: 'randr', 'vidmode'
; type 'redshift -m list' to see all possible values.
; 'randr' is the preferred method, 'vidmode' is an older API.
; but works in some cases when 'randr' does not.
; The adjustment method settings are in a different section.
adjustment-method=randr

; Configuration of the location-provider:
; type 'redshift -l PROVIDER:help' to see the settings.
; ex: 'redshift -l manual:help'
; Keep in mind that longitudes west of Greenwich (e.g. the Americas)
; are negative numbers.
[manual]
lat=23.728592
lon=90.385429

; Configuration of the adjustment-method
; type 'redshift -m METHOD:help' to see the settings.
; ex: 'redshift -m randr:help'
; In this example, randr is configured to adjust screen 1.
; Note that the numbering starts from 0, so this is actually the
; second screen. If this option is not specified, Redshift will try
; to adjust _all_ screens.
[randr]
screen=0
```
