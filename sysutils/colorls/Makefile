COMMENT=	ls(1) that can use color to display file attributes

VERSION=	7.6
DISTNAME=	ls-${VERSION}
PKGNAME=	colorls-${VERSION}
CATEGORIES=	sysutils

MAINTAINER=	Christian Weisgerber <naddy@openbsd.org>

# BSD
PERMIT_PACKAGE=	Yes

SITES=		https://shell.uugrn.org/~naddy/

WANTLIB=	c curses util

NO_TEST=	Yes

# copy file and substitute a string near a CVS keyword
pre-patch:
	sed 's/^\.Dt LS/.Dt COLORLS/' ${WRKSRC}/ls.1 >${WRKSRC}/colorls.1

.include <bsd.port.mk>
