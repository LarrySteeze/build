NAME     = libsdl
TITLE    = libsdl
APP_ID   = org.webosinternals.toolchain.${NAME}
SRC_VER  = 1.2
VERSION  = 1.2-2
MAINTAINER = WebOS Internals <support@webos-internals.org>

SRC_TGZ = http://downloads.help.palm.com/opensource/1.3.5/${NAME}-${SRC_VER}.tgz

.PHONY: package
package: build/.built-${VERSION}

include ../../support/download.mk

.PHONY: stage
stage: build/.staged-${VERSION}

build/.staged-${VERSION}: build/armv7.staged-${VERSION} build/armv6.staged-${VERSION} build/i686.staged-${VERSION}
	touch $@

build/%.staged-${VERSION} : build/%.built-${VERSION}
	mkdir -p ../../staging/$*/usr/include
	cp -rp build/$*/usr/include/* ../../staging/$*/usr/include/
	mkdir -p ../../staging/$*/usr/lib
	cp -rp build/$*/usr/lib/* ../../staging/$*/usr/lib/
	touch $@

.PHONY: unpack
unpack: build/.unpacked-${VERSION}

build/.unpacked-${VERSION}: ${DL_DIR}/${NAME}-${VERSION}.tar.gz
	rm -rf build
	mkdir -p build/armv6 build/armv7 build/i686
	tar -C build -z -x -f $<
	mv build/${NAME}-${SRC_VER} build/src
	${MAKE} SRC_FILE=http://downloads.help.palm.com/opensource/1.3.5/${NAME}-${SRC_VER}-patch.gz \
		LOCAL_FILE=${NAME}-${VERSION}-patch.gz download
	cd build/src; \
		zcat ../../${DL_DIR}/${NAME}-${VERSION}-patch.gz | patch -p1 ; \
		sed -i.orig -e 's/SDL_GL_SWAP_CONTROL,/SDL_GL_SWAP_CONTROL/' include/SDL_video.h
	touch $@

.PHONY: build
build: build/.built-${VERSION}

build/.built-${VERSION}: build/armv7.built-${VERSION} build/armv6.built-${VERSION} build/i686.built-${VERSION}
	touch $@

include ../../support/cross-compile.mk

build/%.built-${VERSION}: build/.unpacked-${VERSION}
	rm -rf build/$*
	( cd build/src ; \
	  CC=${CROSS_COMPILE_$*}gcc \
	  CFLAGS="-I${STAGING_DIR_$*}/usr/include -DPALM=1" \
	  LDFLAGS="-L${STAGING_DIR_$*}/usr/lib -L${STAGING_DIR_$*}/usr/lib/pulse" \
	  ./configure \
	  	--host=${CONFIGURE_HOST_$*} \
		--disable-static \
		--disable-video-x11 \
		--disable-arts \
		--disable-oss \
		--disable-assembly \
		--disable-esd \
		--disable-nas \
		--disable-diskaudio \
		--disable-dummyaudio \
		--disable-mintaudio \
                --disable-video-directfb \
                --disable-video-fbcon \
		--disable-nasm \
		--disable-altivec \
		--disable-ipod \
		--disable-pth \
		--enable-shared ;\
	  ${MAKE} clean all )
	mkdir -p build/$*/usr/include/SDL
	install -m 644 build/src/include/* build/$*/usr/include/SDL/
	mkdir -p build/$*/usr/lib
	install -m 755 build/src/build/.libs/*.so* build/$*/usr/lib/
	touch $@

clobber::
	rm -rf build
