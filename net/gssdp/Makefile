# Created by: Martin Wilke <miwi@FreeBSD.org>
# $FreeBSD$

PORTNAME=	gssdp
PORTVERSION=	0.14.11
CATEGORIES=	net
MASTER_SITES=	GNOME

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Framework for UPnP devices

LICENSE=	LGPL20

BUILD_DEPENDS=	gobject-introspection>=0.6.7:${PORTSDIR}/devel/gobject-introspection
LIB_DEPENDS=	libsoup-2.4.so:${PORTSDIR}/devel/libsoup

OPTIONS_DEFINE=	GTK3
OPTIONS_DEFAULT=GTK3
OPTIONS_SUB=	yes

CONFIGURE_ARGS=	--enable-introspection=yes
CONFIGURE_ENV=	VAPIGEN="" ac_cv_path_VAPIGEN=""
GNU_CONFIGURE=	yes
INSTALL_TARGET=	install-strip
USE_GNOME=	glib20 introspection:build
USE_LDCONFIG=	yes
USES=		gmake libtool pathfix pkgconfig tar:xz

GTK3_CONFIGURE_WITH=	gtk
GTK3_USE=		GNOME=gtk30

.include <bsd.port.mk>
