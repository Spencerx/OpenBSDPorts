COMMENT=		general purpose dynamic array

DISTNAME=		Judy-1.0.5
WRKDIST=		${WRKDIR}/${DISTNAME:L}
PKGNAME=		lib${DISTNAME}
CATEGORIES=		devel
REVISION=		0

SHARED_LIBS +=	Judy                 1.4      # .1.4

HOMEPAGE=		https://judy.sourceforge.net/

# LGPL
PERMIT_PACKAGE=	Yes

SITES=			${SITE_SOURCEFORGE:=judy/}

CONFIGURE_STYLE=	gnu
USE_GMAKE=		Yes

EXAMPLESDIR=		${PREFIX}/share/examples/libJudy

post-install:
	${INSTALL_DATA_DIR} ${EXAMPLESDIR}
	@cd ${WRKSRC}/src/apps/demo; tar cf - * | tar xf - -C ${EXAMPLESDIR}
	@${SUBST_DATA} ${WRKSRC}/src/apps/demo/run_demo ${EXAMPLESDIR}/run_demo

.include <bsd.port.mk>
