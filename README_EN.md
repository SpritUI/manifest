**[中文](https://github.com/SpritUI/manifest/blob/sprit-q/README.md)｜English**

# SpritUI

## What’s SpritUI?

SpritUI is an open source Android project for old people and students, based on LineageOS and AOSP. 

## How to build SpritUI?
> This guide take Debian (Ubuntu) for example. 

### Install requirements 
```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5-dev libsdl1.2-dev libssl-dev libwxgtk3.0-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev 
```

- For Ubuntu versions older than 20.04, need install：`libwxgtk3.0-dev`
- For Ubuntu versions older than 16.04, need install：`libwxgtk2.8-dev`

### Install Repo：

```shell
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
sudo cp ~/bin/repo /bin/repo
sudo chmod a+x /bin/repo
```

### Setting Git Username and e-mail：

```shell
git config --global user.email "xxx@xxx.com"
git config --global user.name "xxx"
```

### Create the work directory

```shell
mkdir ~/SpritUI
cd ~/SpritUI
```

### Initialize the SpritUI source repository
```shell
repo init -u https://github.com/SpritUI/manifest.git -b sprit-q
```

### Download the source code
```shell
repo sync
```

### Prepare the device-specific code
```shell
. build/envsetup.sh
lunch sprit_[device_code]-userdebug
```

### Start the build
```shell
mka bacon
```
