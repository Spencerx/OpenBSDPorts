COMMENT =		high-performance HTTP accelerator

DISTNAME =		varnish-7.7.1

CATEGORIES =		www

SHARED_LIBS =		varnishapi      4.0     # 3.0

HOMEPAGE =		https://www.varnish-cache.org/

MAINTAINER =		Gonzalo L. Rodriguez <gonzalo@openbsd.org>

# BSD
PERMIT_PACKAGE =	Yes

SITES =			https://varnish-cache.org/_downloads/

EXTRACT_SUFX =		.tgz

WANTLIB += c curses execinfo m pcre2-8 pthread readline

MODULES =		lang/python
MODPY_RUNDEP =		No
MODPY_ADJ_FILES =	lib/libvcc/vmodtool.py

BUILD_DEPENDS =		textproc/py-docutils \
			textproc/py-sphinx
LIB_DEPENDS =		devel/pcre2

USE_GMAKE =		Yes
SEPARATE_BUILD =	Yes

# requires to patch configure.ac
AUTOCONF_VERSION =	2.72
AUTOMAKE_VERSION=	1.16
CONFIGURE_STYLE =	autoreconf

CONFIGURE_ENV =		CPPFLAGS="-I${LOCALBASE}/include" \
			LDFLAGS="-L${LOCALBASE}/lib ${LDFLAGS}" \
			PYTHON="${MODPY_BIN}" \
			ax_cv_check_cflags___Werror=no
CONFIGURE_ARGS =	--docdir=${PREFIX}/share/examples/varnish \
			--mandir=${PREFIX}/man \
			--localstatedir=${LOCALSTATEDIR}

TEST_TARGET =		check

.ifdef DEBUG
CONFIGURE_ARGS +=	--enable-debugging-symbols
.endif

# varnishd(1) default is localhost:0 (random port);
# set arbitrary port to make varnishreload(1) work out of the box.
MGTSOCK =		localhost:9999
# varnishd(1) default;  required for varnishreload(1)/varnishadm(1).
MGTSEC =		${LOCALSTATEDIR}/varnish/varnishd/_.secret

SUBST_VARS +=		MGTSOCK \
			MGTSEC

RC =			${FILESDIR}/varnishreload
MAN =			${RC}.1
RCINST =		${PREFIX}/bin/${RC:T}
MANINST =		${PREFIX}/man/man1/${MAN:T}

post-install:
	${SUBST_PROGRAM} ${RC} ${RCINST}
	@ksh -n ${RCINST}
	${SUBST_MAN} ${MAN} ${MANINST}
	@mandoc -Tlint -Wwarning ${MAN}
	rm -f ${PREFIX}/lib/varnish/{vmods,}/*.{a,la}

.include <bsd.port.mk>
