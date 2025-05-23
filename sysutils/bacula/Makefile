# XXX building this port while a version is already installed on the
# system will lead to unexpected hidden dependencies!!!

COMMENT-main=		network backup solution (client)
COMMENT-server=		network backup solution (server)
COMMENT-bat=		network backup solution (gui-client)
COMMENT-mysql=		Bacula libbaccats support for MySQL
COMMENT-pgsql=		Bacula libbaccats support for PostgreSQL
COMMENT-sqlite3=	Bacula libbaccats support for SQLite3

V=			15.0.3
DISTNAME=		bacula-$V
PKGNAME-main=		bacula-client-$V
PKGNAME-server=		bacula-server-$V
PKGNAME-bat=		bacula-bat-$V
PKGNAME-mysql=		bacula-mysql-$V
PKGNAME-pgsql=		bacula-pgsql-$V
PKGNAME-sqlite3=	bacula-sqlite3-$V

CATEGORIES=		sysutils

SHARED_LIBS +=  bac                  11.1
SHARED_LIBS +=  baccfg               10.0
SHARED_LIBS +=  bacfind              9.0
SHARED_LIBS +=  bacsd                3.0
SHARED_LIBS +=  bacsql               9.0

BACCATS_LIBV =	7.0
SHARED_LIBS +=  baccats              ${BACCATS_LIBV}
SHARED_LIBS +=  baccats-mysql        ${BACCATS_LIBV}
SHARED_LIBS +=  baccats-postgresql   ${BACCATS_LIBV}
SHARED_LIBS +=  baccats-sqlite3      ${BACCATS_LIBV}

SITES=			${SITE_SOURCEFORGE:=bacula/}
HOMEPAGE=		http://www.bacula.org/

WANTLIB += c crypto m pthread ssl z ${COMPILER_LIBCXX}

# AGPLv3 with exception for OpenSSL (majority),
# FDL (docs), LGPL (some libraries), and PD
# http://www.bacula.org/7.0.x-manuals/en/main/Bacula_Copyright_Trademark_.html
PERMIT_PACKAGE=		Yes

LOCALSTATEDIR=		${BASELOCALSTATEDIR}/bacula
SYSCONFDIR=		${BASESYSCONFDIR}/bacula
DEBUG_PACKAGES=		${BUILD_PACKAGES}

CONFIGURE_STYLE=	gnu
USE_GMAKE=		Yes
NO_TEST=		Yes

PSEUDO_FLAVORS=		no_bat no_pgsql no_mysql
FLAVOR?=

MULTI_PACKAGES=		-main -server -bat -mysql -pgsql -sqlite3

CONFIGURE_ARGS=		--enable-smartalloc \
			--docdir=${PREFIX}/share/doc/bacula \
			--htmldir=${PREFIX}/share/doc/bacula/html \
			--with-dir-user=_bacula \
			--with-dir-group=_bacula \
			--with-sd-user=_bacula-sd \
			--with-sd-group=_bacula \
			--with-scriptdir=${PREFIX}/libexec/bacula \
			--with-fd-user=root \
			--with-fd-group=wheel \
			--with-pid-dir=/var/run \
			--with-subsys-dir=${LOCALSTATEDIR} \
			--with-working-dir=${LOCALSTATEDIR} \
			--with-bsrdir=${LOCALSTATEDIR} \
			--with-logdir=${LOCALSTATEDIR} \
			--with-sbin-perm=755 \
			--with-lzo=${LOCALBASE} \
			--without-x \
			--disable-nls \
			--disable-conio \
			--enable-readline \
			--with-readline=/usr \
			--with-openssl \
			--with-basename=bacula \
			--with-hostname=bacula.domain.tld \
			--with-sqlite3

MAKE_FLAGS=		NO_ECHO=
USE_LIBTOOL=		gnu# base libtool with Qt5 is in the too-hard basket
LIBTOOL_FLAGS=		--tag=disable-static

CONFIGURE_ENV=		CONFIG_SITE="${PORTSDIR}/infrastructure/db/config.site" \
			MTX=/bin/chio \
			PKG_CONFIG_LIBDIR="${MODQT_LIBDIR}/pkgconfig:${MODQT_LIBDIR}" \
			QMAKE="${MODQT_QMAKE}"

# configure mistakenly assumes xattr support if it finds any of the
# openat() family of functions, so poison the autoconf cache.
# None of these functions are used outside the code for Solaris xattr
# as of 5.0.2.
.for ac_func in openat fstatat unlinkat fchownat futimesat
CONFIGURE_ENV +=	ac_cv_func_${ac_func}=no
.endfor

WANTLIB-main += ${WANTLIB} lzo2 curses readline
LIB_DEPENDS-main=	${LIB_DEPENDS} \
			archivers/lzo2

WANTLIB-server += ${WANTLIB} bac baccats baccfg bacfind lzo2
LIB_DEPENDS-server=	${LIB_DEPENDS} \
			sysutils/bacula,-main \
			bacula-pgsql-*|bacula-mysql-*|bacula-sqlite3-*:sysutils/bacula,-pgsql

WANTLIB-pgsql += pq m ${COMPILER_LIBCXX}
LIB_DEPENDS-pgsql +=	${MODGCC4_CPPLIBDEP} \
			databases/postgresql
RUN_DEPENDS-pgsql +=	databases/postgresql,-contrib

WANTLIB-mysql += m mariadb ${COMPILER_LIBCXX}
LIB_DEPENDS-mysql +=	${MODGCC4_CPPLIBDEP} \
			databases/mariadb

WANTLIB-sqlite3 += sqlite3 m pthread z ${COMPILER_LIBCXX}
LIB_DEPENDS-sqlite3=	${MODGCC4_CPPLIBDEP} \
			databases/sqlite3

MODULES +=		x11/qt5
MODQT_DEPS =		No

WANTLIB-bat += ${WANTLIB} bac baccfg bacfind
WANTLIB-bat += GL Qt5Core Qt5Gui Qt5Widgets qwt
WANTLIB-bat += lib/inotify/inotify

RUN_DEPENDS-bat=	${RUN_DEPENDS} \
			devel/desktop-file-utils
LIB_DEPENDS-bat=	${LIB_DEPENDS} \
			${MODQT_LIB_DEPENDS} \
			devel/libinotify \
			sysutils/bacula,-main \
			x11/qwt

RUN_DEPENDS-server=	lang/gawk

.include <bsd.port.arch.mk>

.if !${BUILD_PACKAGES:M-bat}
CONFIGURE_ARGS +=	--disable-bat
.else
CONFIGURE_ARGS +=	--enable-bat
# something in tray-monitor seems to still depend on this (at least,
# it complains if junked during the build), though it looks like the dep
# is supposed to have been removed by now.
BUILD_DEPENDS +=	x11/qwt
.endif

.if !${BUILD_PACKAGES:M-mysql}
CONFIGURE_ARGS +=	--without-mysql
.else
CONFIGURE_ARGS +=	--with-mysql
.endif

.if !${BUILD_PACKAGES:M-pgsql}
CONFIGURE_ARGS +=	--without-postgresql
.else
CONFIGURE_ARGS +=	--with-postgresql
.endif

pre-configure:
	cd ${WRKSRC}; ${SUBST_CMD} manpages/bat.1 \
		src/qt-console/main.cpp \
		src/qt-console/tray-monitor/tray-monitor.pro.in

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/bacula
	${INSTALL_SCRIPT_DIR} ${PREFIX}/libexec/bacula/updatedb
	${INSTALL_SCRIPT} ${WRKSRC}/updatedb/* ${PREFIX}/libexec/bacula/updatedb
	${INSTALL_SCRIPT} ${WRKSRC}/examples/autochangers/chio-changer-openbsd \
		${PREFIX}/libexec/bacula/chio-changer-openbsd.dist
	cp -pR ${WRKSRC}/examples/reports ${PREFIX}/share/examples/bacula
	rm -f ${PREFIX}/share/examples/bacula/*.${PATCHORIG}
	rm ${PREFIX}/libexec/bacula/updatedb/update*.in
	rm ${PREFIX}/sbin/bacula
# does nothing
	cd ${PREFIX}/libexec/bacula/updatedb && rm update_bacula_tables_8_to_9
# unneeded: SQLite2
	cd ${PREFIX}/libexec/bacula/updatedb && rm update_sqlite_tables_4_to_5 \
		update_sqlite_tables_5_to_6 update_sqlite_tables_6_to_7 \
		update_sqlite_tables_7_to_8 update_sqlite_tables_8_to_9
.if ${BUILD_PACKAGES:M-bat}
# Qt5 linking is broken with base libtool, with GNU libtool for some reason
# the wrappers get installed rather than the object code, so ¯\_(ツ)_/¯
	${INSTALL_PROGRAM} ${WRKSRC}/src/qt-console/tray-monitor/.libs/bacula-tray-monitor ${PREFIX}/sbin
	${INSTALL_PROGRAM} ${WRKSRC}/src/qt-console/.libs/bat ${PREFIX}/sbin

	${INSTALL_DATA_DIR} ${PREFIX}/share/pixmaps
	${INSTALL_DATA} ${WRKSRC}/src/qt-console/images/bat_icon.png \
	    ${PREFIX}/share/pixmaps
	${INSTALL_DATA_DIR} ${PREFIX}/share/applications
	${INSTALL_DATA} ${WRKSRC}/scripts/bat.desktop ${PREFIX}/share/applications
	mv ${PREFIX}/libexec/bacula/bacula-tray-monitor.desktop \
	    ${PREFIX}/share/applications/
.else
	rm ${PREFIX}/man/man1/bat.1
.endif
	mv ${WRKINST}/etc/bacula/* ${PREFIX}/share/examples/bacula/
	rmdir ${WRKINST}/etc/bacula
.if ${BUILD_PACKAGES:M-server}
	rm ${PREFIX}/lib/libbaccats.la
	mv ${PREFIX}/libexec/bacula/query.sql{,.dist}
	mv ${PREFIX}/libexec/bacula/mtx-changer.conf{,.dist}
	rmdir ${WRKINST}/var/bacula
.endif

.include <bsd.port.mk>
