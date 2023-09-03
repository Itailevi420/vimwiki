
# qemu  (kvm enabled)


# quickemu
[project repo](https://github.com/quickemu-project/quickemu)

## Introduction

Quickly create and run highly optimized desktop virtual machines for
Linux, macOS and Windows; with just two commands. You decide what
operating system you want to run and Quickemu will figure out the best
way to do it for you. For example:

```sh
quickget ubuntu-mate 22.04
quickemu --vm ubuntu-mate-22.04.conf
quickemu --vm ubuntu-22.04.conf --display spice
```

## SPICE

The following features are available while using the SPICE protocol:

-   Copy/paste between the guest and host
-   Host file sharing to the guest
-   USB device redirection

To use _SPICE_ add `--display spice` to the Quickemu invocation, this requires
that the **spicy** client is installed, available from the spice-client-gtk
package in Debian/Ubuntu.

e.g🥚
```sh
quickemu --vm ubuntu-22.04.conf --display spice
```

To enable copy/paste with a Windows guest, install [SPICE Windows guest tools](https://www.spice-space.org/download.html) in the guest VM.


## Requirements

-   [QEMU](https://www.qemu.org/) (*6.0.0 or newer*) **with GTK, SDL, SPICE & VirtFS support**
-   [bash](https://www.gnu.org/software/bash/) (*4.0 or newer*)
-   [Coreutils](https://www.gnu.org/software/coreutils/)
-   [EDK II](https://github.com/tianocore/edk2)
-   [grep](https://www.gnu.org/software/grep/)
-   [jq](https://stedolan.github.io/jq/)
-   [LSB](https://wiki.linuxfoundation.org/lsb/start)
-   [procps](https://gitlab.com/procps-ng/procps)
-   [python3](https://www.python.org/)
-   [macrecovery](https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery)
-   [mkisofs](http://cdrtools.sourceforge.net/private/cdrecord.html)
-   [usbutils](https://github.com/gregkh/usbutils)
-   [util-linux](https://github.com/karelzak/util-linux)
-   [sed](https://www.gnu.org/software/sed/)
-   [socat](http://www.dest-unreach.org/socat/)
-   [spicy](https://gitlab.freedesktop.org/spice/spice-gtk)
-   [swtpm](https://github.com/stefanberger/swtpm)
-   [Wget](https://www.gnu.org/software/wget/)
-   [xdg-user-dirs](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/)
-   [xrandr](https://gitlab.freedesktop.org/xorg/app/xrandr)
-   [zsync](http://zsync.moria.org.uk/)
-   [unzip](http://www.info-zip.org/UnZip.html)

### Installing Requirements

For Ubuntu, Arch and nixos systems the
[ppa](https://launchpad.net/~flexiondotorg/+archive/ubuntu/quickemu),
[AUR](https://aur.archlinux.org/packages/quickemu) or
[nix](https://github.com/NixOS/nixpkgs/tree/master/pkgs/development/quickemu)
packaging will take care of the dependencies. For other host
distributions or operating systems it will be necessary to install the
above requirements or their equivalents.

These examples may save a little typing

Debian:

    `sudo apt install qemu bash coreutils ovmf grep jq lsb procps python3 genisoimage usbutils util-linux sed spice-client-gtk swtpm wget xdg-user-dirs zsync unzip`

Fedora:

    `sudo dnf install qemu bash coreutils edk2-tools grep jq lsb procps python3 genisoimage usbutils util-linux sed spice-gtk-tools swtpm wget xdg-user-dirs xrandr unzip`

# Install Quickemu

## Ubuntu

Quickemu is available from a PPA for Ubuntu users. The Quickemu PPA also
includes a back port of QEMU 6.0.0 for 20.04 (Focal) and 21.04
(Hirsute). To install Quickemu and all the dependencies run the
following in a terminal:

``` bash
sudo apt-add-repository ppa:flexiondotorg/quickemu
sudo apt update
sudo apt install quickemu
```

## Other Linux

``` bash
git clone --filter=blob:none https://github.com/wimpysworld/quickemu
cd quickemu
```

Now install all the **Requirements** documented above.



