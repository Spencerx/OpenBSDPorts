COMMENT =		interactive, multi-threaded text mode web browser

DISTNAME =		retawq-0.2.6c
REVISION = 		5
CATEGORIES =		www

HOMEPAGE =		https://retawq.sourceforge.net
SITES =			${SITE_SOURCEFORGE:=retawq/}

# GPLv2
PERMIT_PACKAGE =	Yes

WANTLIB =		c crypto pthread curses ssl

CONFIGURE_STYLE =	simple
CONFIGURE_ARGS = 	--enable-ipv6 --set-tls=2

NO_TEST =		Yes

pre-configure:
	${SUBST_CMD} ${WRKSRC}/docu/retawq.1 ${WRKSRC}/docu/example-config

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/retawq ${PREFIX}/bin
	${INSTALL_MAN} ${WRKSRC}/docu/retawq.1 ${PREFIX}/man/man1
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/retawq
	${INSTALL_DATA} ${WRKSRC}/docu/*html \
		${PREFIX}/share/doc/retawq
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/retawq
	${INSTALL_DATA} ${WRKSRC}/docu/example-config \
		${PREFIX}/share/examples/retawq

.include <bsd.port.mk>
