COMMENT=	displays the status of multi-player Internet Game servers

GH_ACCOUNT=	Unity-Technologies
GH_PROJECT=	qstat
GH_TAGNAME=	v2.17
REVISION=	1

CATEGORIES=	games
MAINTAINER=	Tom Murphy <openbsd@pertho.net>

# Artistic
PERMIT_PACKAGE=	Yes

WANTLIB=	c

MAKE_ENV =		QSTAT_VERSION=${GH_TAGNAME}
CONFIGURE_STYLE =	autoreconf

AUTOCONF_VERSION =	2.71
AUTOMAKE_VERSION =	1.16
AUTORECONF =		env QSTAT_VERSION=${GH_TAGNAME} ./autogen.sh
USE_GMAKE =		yes

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/qstat
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/qstat
	${INSTALL_DATA} ${WRKSRC}/CHANGES.txt ${WRKSRC}/qstatdoc.html \
		${PREFIX}/share/doc/qstat
	${INSTALL_DATA} ${WRKSRC}/qstat.cfg \
		${PREFIX}/share/examples/qstat

.include <bsd.port.mk>
