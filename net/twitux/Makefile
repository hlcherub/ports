# Created by: Arnaud Berthomier
# $FreeBSD$

PORTNAME=	twitux
PORTVERSION=	0.69
PORTREVISION=	7
CATEGORIES=	net
MASTER_SITES=	SF

MAINTAINER=	oz@cyprio.net
COMMENT=	GNOME client for Twitter

LIB_DEPENDS=	libsoup-2.4.so:${PORTSDIR}/devel/libsoup \
		libsexy.so:${PORTSDIR}/x11-toolkits/libsexy \
		libnotify.so:${PORTSDIR}/devel/libnotify \
		libcanberra.so:${PORTSDIR}/audio/libcanberra

USE_XORG=	x11
USE_GNOME=	glib20 gtk20 gconf2 libxml2 gnomedocutils
INSTALLS_OMF=	yes
GNU_CONFIGURE=	yes
USES=		gettext gmake pkgconfig tar:bzip2
CONFIGURE_ENV+=	GMSGFMT="${LOCALBASE}/bin/msgfmt"
GCONF_SCHEMAS=	twitux.schemas
INSTALLS_ICONS=	yes

.include <bsd.port.mk>
