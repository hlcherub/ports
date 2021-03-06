# Created by: Franco Fichtner <franco@opnsense.org>
# $FreeBSD$

PORTNAME=	syslogd
PORTVERSION=	10.1
PORTREVISION=	1
CATEGORIES=	sysutils
DISTFILES=

MAINTAINER=	franco@opnsense.org
COMMENT=	FreeBSD syslogd with additions

OPTIONS_DEFINE=	CLOG INET6 ZMQ
OPTIONS_DEFAULT=CLOG INET6

CLOG_DESC=	Enable clog(1) support
INET6_DESC=	Enable IPv6 support
ZMQ_DESC=	Enable ZMQ support

CLOG_EXTRA_PATCHES=	${PATCHDIR}/extra-clog-support.diff
CLOG_BUILD_DEPENDS=	${LOCALBASE}/include/clog.h:${PORTSDIR}/opnsense/clog
CLOG_RUN_DEPENDS=	clog:${PORTSDIR}/opnsense/clog
CLOG_CFLAGS=		-I${LOCALBASE}/include

INET6_CFLAGS=		-DINET6

ZMQ_EXTRA_PATCHES=	${PATCHDIR}/extra-zmq-support.diff
ZMQ_LIB_DEPENDS=	libczmq.so:${PORTSDIR}/net/czmq
ZMQ_LDFLAGS=		-lczmq -lzmq -lpthread -lstdc++
ZMQ_CFLAGS=		-DWITH_ZMQ

do-extract:
	${CP} -r ${FILESDIR}/src ${WRKSRC}

.include <bsd.port.mk>
