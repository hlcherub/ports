# Created by: DarwinSurvivor <darwinsurvivor@gmail.com>
# $FreeBSD$

PORTNAME=	notmuch
PORTVERSION=	0.19
CATEGORIES=	mail
MASTER_SITES=	http://notmuchmail.org/releases/

MAINTAINER=	ross@rosstimson.com
COMMENT=	Thread-based email index, search, and tagging application

LICENSE=	GPLv3

BUILD_DEPENDS=	sphinx-build:${PORTSDIR}/textproc/py-sphinx
LIB_DEPENDS=	libgmime-2.6.so:${PORTSDIR}/mail/gmime26 \
		libxapian.so:${PORTSDIR}/databases/xapian-core \
		libtalloc.so:${PORTSDIR}/devel/talloc

OPTIONS_DEFINE=	BASH EMACS ZSH
BASH_DESC=	Install bash completion (requires shells/bash-completion)
EMACS_DESC=	Install EMACS lisp files (requires emacs)
ZSH_DESC=	Install zsh completion
OPTIONS_SUB=	yes

BASH_BUILD_DEPENDS=	bash-completion>=1.90:${PORTSDIR}/shells/bash-completion
BASH_RUN_DEPENDS=	${BASH_BUILD_DEPENDS}
BASH_CONFIGURE_OFF=	--without-bash-completion
EMACS_CONFIGURE_OFF=	--without-emacs
EMACS_CONFIGURE_ON=	--emacslispdir=${PREFIX}/${EMACS_SITE_LISPDIR} \
			--emacsetcdir=${PREFIX}/${EMACS_SITE_LISPDIR}
ZSH_CONFIGURE_OFF=	--without-zsh-completion

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MEMACS}
USE_EMACS=	yes
.endif

HAS_CONFIGURE=	yes
USES=		pkgconfig python:build gmake
CONFIGURE_ARGS=	--prefix=${PREFIX} --mandir=${MANPREFIX}/man
USE_LDCONFIG=	yes

MAKE_ENV+=		PYTHONCMD=${PYTHON_CMD}

.include <bsd.port.pre.mk>

.if ${OSVERSION} < 900044
IGNORE=	requires zlib at least 1.2.5
.endif

.include <bsd.port.post.mk>
