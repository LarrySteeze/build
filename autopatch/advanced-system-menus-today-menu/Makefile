NAME = $(shell basename $(shell pwd))
PATCH = advanced/${NAME}.patch
FILES = advanced/${NAME}.tar.gz
TITLE = Advanced System Menus - Today Menu
DESCRIPTION = * Requires Advanced System Menus Framework patch to function properly!<br/><br/>Adds today menu in the center off top bar. Today menu offers a quick view of your calendar events for the current day and for the next day. Menu can be edited to show events only from certain calendars.
CATEGORY = Advanced
VERSIONS = 2.1.0-230 2.1.1-25 2.1.2-33 2.2.0-13 2.2.4-10
ICON = http://www.webos-internals.org/images/f/f9/Icon_WebOSInternals_Patch.png
SCREENSHOTS = [ \"http://www.webos-internals.org/images/8/8c/AdvancedSystemMenusTodayMenu.png\",\"http://www.webos-internals.org/images/8/88/AdvancedSystemMenusTodayMenuEdit.png\" ]
META_SUB_VERSION = 1

include ../common.mk

include ../modifications.mk

MAINTAINER = sconix
HOMEPAGE = http://forums.precentral.net/enlightened-linux-solutions/269207-patch-advanced-system-menus-2-x.html

POSTINSTALLFLAGS = RestartDevice
POSTUPDATEFLAGS  = RestartDevice
POSTREMOVEFLAGS  = RestartDevice
