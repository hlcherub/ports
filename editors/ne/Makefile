# Created by: Andrej Zverev <az@inec.ru>
# $FreeBSD$

PORTNAME=	ne
PORTVERSION=	2.6
CATEGORIES=	editors
MASTER_SITES=	http://ne.di.unimi.it/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Nice and powerful editor

LICENSE=	GPLv3

BUILD_WRKSRC=	${WRKSRC}/src

USES=		gmake makeinfo perl5
USE_PERL5=	build
MAKEFILE=	makefile
ALL_TARGET=	${PORTNAME}
MAKE_ARGS=	CC="${CC}" \
		CFLAGS="${CFLAGS}" \
		LDFLAGS="-lgnuregex" \
		NE_GLOBAL_DIR="${DATADIR}"

INFO=		${PORTNAME}
PORTDOCS=	*
PLIST_FILES=	bin/${PORTNAME} \
		man/man1/${PORTNAME}.1.gz \
		%%DATADIR%%/default.keys %%DATADIR%%/default.menus \
		%%DATADIR%%/syntax/4gl.jsf %%DATADIR%%/syntax/ada.jsf \
		%%DATADIR%%/syntax/ant.jsf %%DATADIR%%/syntax/batch.jsf \
		%%DATADIR%%/syntax/asm.jsf %%DATADIR%%/syntax/awk.jsf \
		%%DATADIR%%/syntax/c.jsf %%DATADIR%%/syntax/cobol.jsf \
		%%DATADIR%%/syntax/classic_pascal.jsf \
		%%DATADIR%%/syntax/comment_todo.jsf \
		%%DATADIR%%/syntax/conf.jsf %%DATADIR%%/syntax/csh.jsf \
		%%DATADIR%%/syntax/csharp.jsf %%DATADIR%%/syntax/debian.jsf \
		%%DATADIR%%/syntax/css.jsf %%DATADIR%%/syntax/diff.jsf \
		%%DATADIR%%/syntax/elixir.jsf %%DATADIR%%/syntax/erb.jsf \
		%%DATADIR%%/syntax/erlang.jsf %%DATADIR%%/syntax/git-commit.jsf \
		%%DATADIR%%/syntax/fortran.jsf %%DATADIR%%/syntax/haskell.jsf \
		%%DATADIR%%/syntax/go.jsf %%DATADIR%%/syntax/haml.jsf \
		%%DATADIR%%/syntax/html.jsf %%DATADIR%%/syntax/java.jsf \
		%%DATADIR%%/syntax/htmlerb.jsf %%DATADIR%%/syntax/ini.jsf \
		%%DATADIR%%/syntax/iptables.jsf %%DATADIR%%/syntax/js.jsf \
		%%DATADIR%%/syntax/joerc.jsf %%DATADIR%%/syntax/jsf.jsf \
		%%DATADIR%%/syntax/jsf_check.jsf %%DATADIR%%/syntax/lisp.jsf \
		%%DATADIR%%/syntax/json.jsf %%DATADIR%%/syntax/md.jsf \
		%%DATADIR%%/syntax/lua.jsf %%DATADIR%%/syntax/m4.jsf \
		%%DATADIR%%/syntax/mail.jsf %%DATADIR%%/syntax/mason.jsf \
		%%DATADIR%%/syntax/matlab.jsf %%DATADIR%%/syntax/ocaml.jsf \
		%%DATADIR%%/syntax/pascal.jsf %%DATADIR%%/syntax/perl.jsf \
		%%DATADIR%%/syntax/php.jsf %%DATADIR%%/syntax/ps.jsf \
		%%DATADIR%%/syntax/powershell.jsf %%DATADIR%%/syntax/prolog.jsf \
		%%DATADIR%%/syntax/properties.jsf %%DATADIR%%/syntax/puppet.jsf \
		%%DATADIR%%/syntax/python.jsf %%DATADIR%%/syntax/rexx.jsf \
		%%DATADIR%%/syntax/ruby.jsf %%DATADIR%%/syntax/sed.jsf \
		%%DATADIR%%/syntax/sh.jsf %%DATADIR%%/syntax/skill.jsf \
		%%DATADIR%%/syntax/sieve.jsf %%DATADIR%%/syntax/typescript.jsf \
		%%DATADIR%%/syntax/sml.jsf %%DATADIR%%/syntax/spec.jsf \
		%%DATADIR%%/syntax/sql.jsf %%DATADIR%%/syntax/tabs.jsf \
		%%DATADIR%%/syntax/tcl.jsf %%DATADIR%%/syntax/tex.jsf \
		%%DATADIR%%/syntax/texinfo.jsf %%DATADIR%%/syntax/troff.jsf \
		%%DATADIR%%/syntax/txt2tags.jsf %%DATADIR%%/syntax/verilog.jsf \
		%%DATADIR%%/syntax/whitespace.jsf %%DATADIR%%/syntax/yaml.jsf \
		%%DATADIR%%/syntax/vhdl.jsf %%DATADIR%%/syntax/xml.jsf

OPTIONS_DEFINE=	DEBUG DOCS

.include <bsd.port.options.mk>

.if ! ${PORT_OPTIONS:MDEBUG}
CFLAGS+=	-DNODEBUG
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|tmpnam(|mkstemp(|g' ${BUILD_WRKSRC}/actions.c
	@${REINPLACE_CMD} -e 's|"regex\.h"|<gnu/regex.h>|g' \
		${BUILD_WRKSRC}/ne.c \
		${BUILD_WRKSRC}/search.c
	@${REINPLACE_CMD} -e '/[[:space:]]regex.o/d ; \
		 s|regex.h||g' ${BUILD_WRKSRC}/makefile

post-build:
	cd ${WRKSRC}/doc && makeinfo ${PORTNAME}.texinfo

do-install:
	${INSTALL_PROGRAM} ${BUILD_WRKSRC}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/doc/${PORTNAME}.1 \
		${STAGEDIR}${MANPREFIX}/man/man1
	${INSTALL_DATA} ${WRKSRC}/doc/${PORTNAME}.info \
		${STAGEDIR}${PREFIX}/${INFO_PATH}
	@${MKDIR} ${STAGEDIR}${DATADIR}
	${INSTALL_DATA}	${WRKSRC}/doc/default.* ${STAGEDIR}${DATADIR}
	(cd ${WRKSRC} && ${COPYTREE_SHARE} syntax ${STAGEDIR}${DATADIR})
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	(cd ${WRKSRC} && ${INSTALL_DATA} CHANGES NEWS README \
		doc/${PORTNAME}.pdf doc/${PORTNAME}.txt ${STAGEDIR}${DOCSDIR})
	(cd ${WRKSRC}/doc && ${COPYTREE_SHARE} html ${STAGEDIR}${DOCSDIR})

.include <bsd.port.mk>
