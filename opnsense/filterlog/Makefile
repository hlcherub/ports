# Created by: Franco Fichtner <franco@opnsense.org>
# $FreeBSD$

PORTNAME=	filterlog
PORTVERSION=	0.2
CATEGORIES?=	sysutils
MASTER_SITES=	# empty
DISTFILES=	# none
EXTRACT_ONLY=	# empty

MAINTAINER=	franco@opnsense.org
COMMENT=	Parse pflog(4) output

do-extract:
	${MKDIR} ${WRKSRC}
	${CP} ${FILESDIR}/* ${WRKSRC}

.include <bsd.port.mk>
