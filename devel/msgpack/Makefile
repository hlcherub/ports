# $FreeBSD$

PORTNAME=	msgpack
PORTVERSION=	1.0.0
DISTVERSIONPREFIX=	cpp-
CATEGORIES=	devel

MAINTAINER=	kuriyama@FreeBSD.org
COMMENT=	MessagePack implementation for C and C++

LICENSE=	APACHE20

USE_GITHUB=	yes
GH_PROJECT= msgpack-c

USES=		libtool:build autoreconf:build

GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes

.include <bsd.port.pre.mk>

.if ${ARCH} == "sparc64"
# required for __sync _* atomic operations on sparc
USE_GCC=	yes
.endif

.if ${ARCH} == "i386"
# Mayby not working on i386/i486/i586...
CONFIGURE_ARGS=	CFLAGS="${CFLAGS} -march=i686" CXXFLAGS="${CXXFLAGS} -march=i686"
.endif

pre-configure:
	cd ${WRKSRC} && ./bootstrap

.include <bsd.port.post.mk>
