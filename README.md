G-Core-Labs-Baremetal
===============

The G-Core-Labs-Baremetal is set of diskimage-builder elements 
required to build custom cloud image suitable for Baremetal
Service.


The main noticable changes to default cloud images are:
- Bonding support
- EFI support
- Cloud-init that knows about VLANs 

Getting Started
===============

- Clone this repo to your working directory
- Install diskimage-builder from pip
- Install any packages you missing to run diskimage-builder
- Make any changes to elements if required
- Run diskimage-builder
- Upload image to your cloud

Examples
===============

Centos 7 
-

```
pipenv shell
pip install diskimage-builder

git clone https://github.com/G-Core/baremetal-dib-elements.git
export ELEMENTS_PATH="./baremetal-dib-elements"
export DIB_RELEASE="7"
export DIB_AVOID_PACKAGES_UPDATE=1
export DIB_CLOUD_INIT_DATASOURCES="ConfigDrive, OpenStack"
export DIB_BOOTLOADER_SERIAL_CONSOLE=""
export DIB_BOOTLOADER_DEFAULT_CMDLINE=" "
export OS_ELEMENTS="vm cloud-init-datasources block-device-efi dracut-regenerate"
disk-image-create centos centos-ironic ${OS_ELEMENTS} -o centos-ironic -t raw
```

Centos 8 
-

```
pipenv shell
pip install diskimage-builder

git clone https://github.com/G-Core/baremetal-dib-elements.git
export ELEMENTS_PATH="./baremetal-dib-elements"
export DIB_RELEASE="8"
export DIB_AVOID_PACKAGES_UPDATE=1
export DIB_CLOUD_INIT_DATASOURCES="ConfigDrive, OpenStack"
export DIB_BOOTLOADER_SERIAL_CONSOLE=""
export DIB_BOOTLOADER_DEFAULT_CMDLINE=" "
export OS_ELEMENTS="vm cloud-init-datasources block-device-efi dracut-regenerate"
disk-image-create centos centos-ironic ${OS_ELEMENTS} -o centos-ironic -t raw
```

Notices
===============

You may found sources of patched cloud-init [here](https://github.com/G-Core/baremetal-cloud-init/tree/gcore/)
