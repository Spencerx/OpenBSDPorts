COMMENT =	encrypted SQLite database

GH_ACCOUNT =	sqlcipher
GH_PROJECT =	sqlcipher
GH_TAGNAME =	v4.6.1
REVISION =	1

SHARED_LIBS +=  sqlcipher                 2.0 # 8.6

CATEGORIES =	databases

HOMEPAGE =	https://www.zetetic.net/sqlcipher/

# PD and BSD
PERMIT_PACKAGE =	Yes

WANTLIB +=		c crypto curses m pthread readline z

CONFIGURE_STYLE =	gnu

CONFIGURE_ARGS +=	--enable-tempstore=yes \
			--disable-editline \
			--disable-tcl
CONFIGURE_ENV +=	TCLSH_CMD=${MODTCL_BIN}

NO_TEST =		Yes

CFLAGS +=		-DSQLITE_HAS_CODEC -DOMIT_MEMLOCK

MODULES =		lang/tcl
MODTCL_VERSION =	8.6
BUILD_DEPENDS =		${MODTCL_BUILD_DEPENDS}

.include <bsd.port.mk>
