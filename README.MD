**中文｜[English](https://github.com/SpritUI/manifest/blob/sprit-q/README_EN.md)**

# SpritUI
## 什么是 SpritUI ？
SpritUI是一个为老人、学生群体量身打造的开源类原生 Android 项目，基于LineageOS和AOSP。

## 如何编译 SpritUI ？
> 该向导以 Debian 系 Linux 发行版 Ubuntu 为例
### 安装相关依赖
```shell
sudo apt-get install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git gnupg gperf imagemagick lib32ncurses5-dev lib32readline-dev lib32z1-dev liblz4-tool libncurses5 libncurses5-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev
```
- 低于20.04的Ubuntu，还需安装：`libwxgtk3.0-dev`
- 低于16.04的Ubuntu，还需安装：`libwxgtk2.8-dev`

### 安装repo：
```shell
mkdir -p ~/bin
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
sudo cp ~/bin/repo /bin/repo
sudo chmod a+x /bin/repo
```

### 设置Git用户名及邮箱：
```shell
git config --global user.email "xxx@xxx.com"
git config --global user.name "xxx"
```

### 新建工作区
> 这里的工作区指存放 SpritUI 源码的路径

```shell
mkdir ~/SpritUI
cd ~/SpritUI
```

### 初始化仓库
```shell
# depth=1 表示不同步历史提交
# [方括号]内为可选参数，可以根据网络情况按需使用。
repo init -u https://github.com/SpritUI/android.git -b sprit-q [--depth=1]
```
### 同步源码
```shell
# -j参数为下载线程数，不带该参数默认自动分配线程，-l参数用于更新本地存储库，--fail-fast参数可以处理上次repo时由于网络原因导致的同步失败问题，--force-sync参数忽略本地修改，强制同步git仓库的内容。
repo sync [-j8 --fail-fast --force-sync]
```

### 开始编译
```shell
# 确保当前所在目录为 SpritUI 源码根目录

# 初始化编译环境
. build/envsetup.sh

# 初始化编译设备
lunch sprit_[您的设备代号]-userdebug
# 您也可以使用该命令初始化编译设备
breakfast [您的设备代号]

# 开始编译
mka bacon
```
