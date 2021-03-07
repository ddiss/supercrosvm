## supercrosvm

This is a Git superproject carrying [crosvm](https://chromium.googlesource.com/chromiumos/platform/crosvm/) source and most dependencies, all as Git submodules pointing to the *current* official upstream repository URLs.

### build

The following example was done using openSUSE Leap 15.2 / SLES 15sp2.
Install some dependencies:
```
# sudo zypper in libcap-devel libfdt-devel libgbm-devel wayland-protocols-devel libusb-1_0-devel
# sudo zypper ar --refresh https://download.opensuse.org/repositories/devel:/languages:/rust/openSUSE_Leap_15.2/ obs_rust
# sudo zypper in -r obs_rust rust
# cd supercrosvm/platform/crosvm
# cargo build --no-default-features
```
The distribution rust compiler may be a little out of date, so the procedure above should install the latest from the build service.
`--no-default-features` will provide a minimal build lacking many graphics and audio features.

### run

The example below boots a Linux kernel bzImage built from source, and an initramfs image generated via dracut.
**Warning:** crosvm sandboxing is disabled.
```
# cd supercrosvm/platform/crosvm
# ./target/debug/crosvm run --disable-sandbox -i /home/ddiss/initramfs.img /home/ddiss/bzImage 
```
