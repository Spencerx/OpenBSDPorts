COMMENT=	library for delta compression of streams

V =		2.3.4
DISTNAME =	librsync-${V}

SHARED_LIBS =	rsync	5.1

# wrong category really, this does not handle the rsync network protocol
CATEGORIES=	net

HOMEPAGE=	https://librsync.github.io/

# LGPLv2.1+
PERMIT_PACKAGE=	Yes

WANTLIB += b2 c popt iconv intl

SITES =		https://github.com/librsync/librsync/releases/download/v${V}/

MODULES=	devel/cmake

LIB_DEPENDS=	devel/popt \
		security/libb2

CONFIGURE_ARGS=	-DUSE_LIBB2=ON

post-install:
	${INSTALL_MAN} ${WRKSRC}/doc/rdiff.1 ${PREFIX}/man/man1
	${INSTALL_MAN} ${WRKSRC}/doc/librsync.3 ${PREFIX}/man/man3

.include <bsd.port.mk>
