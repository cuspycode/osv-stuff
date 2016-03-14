# TomEE deployment on OSv

Based on Tomasz Grabiec's tomcat build project (but not its tomcat image), using TomEE 1.7.4 instead of Tomcat.

This is still a bit raw, and I haven't attempted to replicate any of the patches in the original osv-tomcat project.

Prerequisites:
- Install [capstan](https://github.com/cloudius-systems/capstan) on your dev host (the binary install is fine).
  You can optionally install OSv and capstan from sources found in the relevant
  [cloudius-systems](https://github.com/cloudius-systems) GitHub repos.

How to build:
- Clone this repo and cd to the `tomee` folder.
- Do `capstan build` to create the tomee image. This is optional, the build step will happen
  automatically the first time you do `capstan run`.

Optionally change the download URL in the file [GET](tomee/GET) to a mirror if things seem slow.

How to run:
- Do `capstan run -f 8080:8080` to run an instance in qemu, forwarding its port 8080 to the hypervisor's 8080.
  See the OSv docs for instructions on how to run on a different hypervisor (e.g. VirtualBox or AWS).

To add your own configuration and WAR files etc, edit `Makefile` and add commands to copy stuff to `ROOTFS/usr/tomee` in the `module` target.
