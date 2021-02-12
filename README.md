# packettracer-7.3.1

Installation package of packet tracer 7.3.1 based on the AUR repository

## Compile and Install

- Download .deb archive from [PacketTracer_731_amd64.deb](https://www.dropbox.com/s/m2u3l7y5nyoupyk/PacketTracer_731_amd64.deb?dl=0) on Dropbox or download from official site [Linux Desktop Version 7.3.1 English - netcad](https://www.netacad.com/portal/resources/file/24eeaa30-1d54-4073-822d-e48f6bdfbe15)
- Copy .deb archive to root dir of this project
- Run command: `sha512sum PacketTracer_731_amd64.deb` and compare the hash with the first hash within PKGBUILD. If different, replace it with the command result.
- Compile using the command: `makepkg`
- If everything went well, the file **_packettracer-7.3.1-1-x86_64.pkg.tar.zst_** will be generated
- Install using the command:

  ```shell
  sudo pacman -U packettracer-7.3.1-1-x86_64.pkg.tar.zst
  ```

## Reference

- The official maintainer of the package at AUR [pinned comment](https://aur.archlinux.org/packages/packettracer/#pinned-723200)
