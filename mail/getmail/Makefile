COMMENT=	IMAP/POP3/SDPS mail retriever

GH_ACCOUNT=	getmail6
GH_PROJECT=	getmail6
GH_TAGNAME=	v6.19.08
MODPY_DISTV=	6.19.8
PKGNAME=	getmail-${MODPY_DISTV}
CATEGORIES=	mail

# https://github.com/getmail6/getmail6
HOMEPAGE=	https://getmail6.org/

MAINTAINER=	Martin Ziemer <horrad@horrad.de>

# GPLv2
PERMIT_PACKAGE=	Yes

MODULES=	lang/python
MODPY_PYBUILD=	setuptools
NO_TEST=	Yes

EXDIR=		${PREFIX}/share/examples/getmail

post-install:
	${INSTALL_DATA_DIR} ${EXDIR}
	${INSTALL_DATA} ${WRKDIST}/docs/getmailrc-examples ${EXDIR}

.include <bsd.port.mk>
