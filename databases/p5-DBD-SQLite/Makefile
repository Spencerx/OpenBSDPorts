COMMENT=		SQLite drivers for the Perl DBI

MODULES=		cpan
DISTNAME=		DBD-SQLite-1.76
CATEGORIES=		databases
EPOCH=			0

MAINTAINER=		Robert Nagy <robert@openbsd.org>

# artistic
PERMIT_PACKAGE=	Yes

WANTLIB += c perl sqlite3

BUILD_DEPENDS =		databases/p5-DBI>=1.57
RUN_DEPENDS =		databases/p5-DBI>=1.57
LIB_DEPENDS =		databases/sqlite3

CONFIGURE_ARGS=		SQLITE_LOCATION=${LOCALBASE}
MAKE_FLAGS=		CC='${CC}' \
			LD='${CC}'

MAKE_ENV +=		AUTOMATED_TESTING=1

post-extract:
	rm ${WRKSRC}/sqlite3.{c,h}

.include <bsd.port.mk>
