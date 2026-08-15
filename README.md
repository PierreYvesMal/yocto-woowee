# REPO IN PROGRESS
# TODO
[] Update git tracking to match yocto way (also see Setup section)  


# Setup
[Yocto Project Quick Build](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)
## Dependencies
```
sudo apt-get install build-essential chrpath cpio debianutils diffstat file gawk gcc git iputils-ping libacl1 libcrypt-dev locales python3 python3-git python3-jinja2 python3-pexpect python3-pip python3-subunit socat texinfo unzip wget xz-utils zstd
```
## Locale
Should be en_US.utf8
```
locale --all-locales | grep en_US.utf8
```
## Get bitbake
```
git clone https://git.openembedded.org/bitbake
```
## Clone current repo
```
git clone 
```
## Setup 
TODO something like  
`./bitbake/bin/bitbake-setup init /path/to/your/my-project.conf.json \
    --source-overrides /path/to/your/sources-fixed-revisions.json `
[bitbake setup config](https://docs.yoctoproject.org/bitbake/singleindex.html#document-bitbake-user-manual/bitbake-user-manual-environment-setup)

# build
```
bitbake core-image-base
```
# flash

[24 Creating Partitioned Images Using Wic](https://docs.yoctoproject.org/dev-manual/wic.html)
```
bitbake wic-native -c addto_recipe_sysroot #makes oe-run-native wic-native wic available
umount /dev/sdc[12]
sudo chmod a+rw /dev/sdc
wic write tmp/deploy/images/raspberrypi5/core-image-base-raspberrypi5.rootfs.wic /dev/sdc --expand 1:0,2:29G # using the .bashrc alias wic="oe-run-native wic-native wic"
```
note: --expand auto not working