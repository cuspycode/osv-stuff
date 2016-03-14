# TomEE deployment on OSv

Based on Tomasz Grabiec's tomcat build project (but not its tomcat image), using TomEE 1.7.4 instead of Tomcat.

This is still a bit raw, and I haven't attempted to replicate any of the patches in the original osv-tomcat project.

How to build:
- Install the OSv development environment on your build host.
- Install capstan on your build host (the binary install is fine).
- Download the `tomee` folder and cd to it.
- Do `capstan build` to create the tomee image.

How to run:
- Do `capstan run -f 8080:8080` to run an instance in qemu, forwarding its port 8080 to the hypervisor's 8080.

To add your own configuration and WAR files etc, edit `Makefile` and add commands to copy stuff to `ROOTFS/usr/tomee` in the `module` target.
