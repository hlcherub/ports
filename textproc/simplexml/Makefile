# Created by: Konstantin Lepa <konstantin.lepa@gmail.com>
# $FreeBSD$

PORTNAME=	simplexml
PORTVERSION=	1.0.1
PORTREVISION=	1
CATEGORIES=	textproc
MASTER_SITES=	http://bitbucket.org/klepa/simplexml/get/
DISTNAME=	${PORTVERSION}
DIST_SUBDIR=	${PORTNAME}

MAINTAINER=	konstantin.lepa@gmail.com
COMMENT=	C++ XML parser library

LIB_DEPENDS=	libexpat.so:${PORTSDIR}/textproc/expat2

USES=		cmake iconv
USE_LDCONFIG=	yes

WRKSRC=		${WRKDIR}/${PORTNAME}

.if defined(WITH_DEBUG)
CMAKE_ARGS+=	-DDEBUG_MODE:BOOL=ON
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|/usr/local|${LOCALBASE}|; \
		/set.*CMAKE_BUILD_TYPE/d' ${WRKSRC}/CMakeLists.txt

.include <bsd.port.mk>
