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