# RedressOS
WIP Custom Android UI Based on LineageOS.
<img width="1920" height="1080" alt="RedressBanner" src="https://github.com/user-attachments/assets/7c05eae9-d719-456d-9d4c-ec0de7c6bd0f" />
RedressOS is a custom rom based on LineageOS made by soil.
# Building
You'll need to get familiar with [Source Control Tools](https://source.android.com/setup/develop).
Then you will install the following dependencies: (in case of Ubuntu 24.04)
```
sudo apt install bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick protobuf-compiler python3-protobuf lib32readline-dev lib32z1-dev libdw-dev libelf-dev lz4 libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev openjdk-8-jdk python-is-python3 android-sdk-platform-tools && wget https://archive.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.3-2_amd64.deb && sudo dpkg -i libtinfo5_6.3-2_amd64.deb && rm -f libtinfo5_6.3-2_amd64.deb && wget https://archive.ubuntu.com/ubuntu/pool/universe/n/ncurses/libncurses5_6.3-2_amd64.deb && sudo dpkg -i libncurses5_6.3-2_amd64.deb && rm -f libncurses5_6.3-2_amd64.deb
```
Create the needed directories:
```
mkdir -p ~/bin && mkdir -p ~/redress
```
then install the repo command:
```
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo && chmod a+x ~/bin/repo
```
After this close your terminal and open it again

Given that repo requires you to identify yourself to sync Android, run the following commands to configure your git identity:
```
git config --global user.email "you@example.com"
```
```
git config --global user.name "Your Name"
```
Due to their size, some repos are configured for lfs or Large File Storage. To make sure your distribution is prepared for this, run:
```
git lfs install
```
To avoid duplicated Change-Id: trailers in commit messages, especially when cherry-picking changes, make Change-Id: a known trailer to git:
```
git config --global trailer.changeid.key "Change-Id"
```
Turn on caching to speed up builds:
```
export USE_CCACHE=1
```
```
export CCACHE_EXEC=/usr/bin/ccache
```
```
ccache -M 50G
```
then add the first 2 export lines to your bashrc file

Now to initialize RedressOS trees run:
```
cd redress && repo init -u https://github.com/RedressOSAndroid/android.git -b lineage-22.2 --git-lfs --no-clone-bundle
```
then to start downloading everything:
```
repo sync
```
Then to start building for your device, see the LineageOS Wiki.
