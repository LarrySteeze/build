NAME = $(shell basename $(shell pwd))
TITLE = F4 Phantom (TouchPad)
DEVICE = touchpad
CATEGORY = Alpha
VERSIONS = 3.0.4-79
APPINFO_DESCRIPTION = The latest beta kernel from uNiXpSyChO.<br><br>\
Features:<br> * 1.8GHz<br> * Full-time dual-core<br> * autogroup process scheduling<br> * CFS<br> * BFQ, V(R), SIO<br> * CIFS, NFS, iSCSI, ATA over Ethernet<br> * EXT4<br><br>\
For more information, visit ${HOMEPAGE}<br>
DESCRIPTION = ${APPINFO_DESCRIPTION}<br>${KERNEL_DISCLAIMER}
APPINFO_CHANGELOG = [ \
{ "version" : "${WEBOS_VERSION}-79", "log" : [ "add load polling for power saver. exclude powerd when in power saver. disable power saver when turbo mode enabled and vice versa." ] }, \
{ "version" : "${WEBOS_VERSION}-78", "log" : [ "update sysfs for Govnah support." ] }, \
{ "version" : "${WEBOS_VERSION}-73", "log" : [ "online or offline cpu when changing sysfs. fix power save logic when enabled/disabled. remove unscalable freqs and voltages in arrays when setting in sysfs. make powersaver do the correct thing. merge override modules." ] }, \
{ "version" : "${WEBOS_VERSION}-60", "log" : [ "revert: increase bus bandwidth." ] }, \
{ "version" : "${WEBOS_VERSION}-57", "log" : [ "increase bus bandwidth." ] }, \
{ "version" : "${WEBOS_VERSION}-56", "log" : [ "reintroduce lcd_state again to force cpu online. hotplug patches. ARM cache updates." ] }, \
{ "version" : "${WEBOS_VERSION}-50", "log" : [ "add workaround for power_saver not setting governor until function is finished. add EXT4 support." ] }, \
{ "version" : "${WEBOS_VERSION}-48", "log" : [ "fix lcd state" ] }, \
{ "version" : "${WEBOS_VERSION}-47", "log" : [ "add iSCSI. fix wifi sleep. add power saver mode (off by default, changeable in sysfs). add lcd state." ] }, \
{ "version" : "${WEBOS_VERSION}-46", "log" : [ "add DSCP TOS. add jhash3." ] }, \
{ "version" : "${WEBOS_VERSION}-45", "log" : [ "fix silly mistake for override module loading." ] }, \
{ "version" : "${WEBOS_VERSION}-44", "log" : [ "Initial release. UTF8, ATA over Ethernet added. sysfs to enable or disable turbo_mode (fulltime dualcore)." ] }, \
]
CHANGELOG = \
${WEBOS_VERSION}-79: add load polling for power saver. exclude powerd when in power saver. disable power saver when turbo mode enabled and vice versa.<br>\
${WEBOS_VERSION}-78: update sysfs for Govnah support.<br>\
${WEBOS_VERSION}-73: online or offline cpu when changing sysfs. fix power save logic when enabled/disabled. remove unscalable freqs and voltages in arrays when setting in sysfs. make powersaver do the correct thing. merge override modules.<br>\
${WEBOS_VERSION}-60: revert: increase bus bandwidth.<br>\
${WEBOS_VERSION}-57: increase bus bandwidth.<br>\
${WEBOS_VERSION}-56: reintroduce lcd_state again to force cpu online. hotplug patches. ARM cache updates.<br>\
${WEBOS_VERSION}-50: add workaround for power_saver not setting governor until function is finished. add EXT4 support.<br>\
${WEBOS_VERSION}-48: fix lcd state<br>\
${WEBOS_VERSION}-47: add iSCSI. fix wifi sleep. add power saver mode (off by default, changeable in sysfs). add lcd state.<br>\
${WEBOS_VERSION}-46: add DSCP TOS. add jhash3.<br>\
${WEBOS_VERSION}-45: fix silly mistake for override module loading.<br>\
${WEBOS_VERSION}-44: Initial release. UTF8, ATA over Ethernet added. sysfs to enable or disable turbo_mode (fulltime dualcore).<br>

HOMEPAGE = http://www.webos-internals.org/wiki/Application:PsychoKernel
SRC_GIT = git://git.webos-internals.org/kernels/patches.git
KERNEL_PATCHES = identification/mkcompile_h.patch \
		 psychobuild/F4.patch \
		 psychobuild/override.patch \
		 psychobuild/F4-logo.patch \
		 psychobuild/fbconsole.patch \
		 psychobuild/comptune.patch \
		 psychobuild/cpu_alignment.patch \
		 psychobuild/iosched-bundle.patch \
		 psychobuild/iosched-deadline.patch \
		 psychobuild/cache-p1.patch \
		 psychobuild/sched-p1.patch \
		 psychobuild/clock-p1.patch \
		 psychobuild/mmc-p1.patch \
		 psychobuild/mmc-p2.patch \
		 memory/tmc_mem.patch \
		 psychobuild/autogroup.patch \
		 psychobuild/jhash3.patch

TYPE = Kernel

include ../../support/kernel.mk

KERNEL_DEFCONFIG = psychobuild/F4.config

