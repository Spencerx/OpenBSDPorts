COMMENT =	user interface library from pwmt
DISTNAME =	girara-0.4.5

SHARED_LIBS += girara-gtk3               2.0 # 3.1

EXTRACT_SUFX =	.tar.xz

CATEGORIES =	x11
HOMEPAGE =	https://pwmt.org/projects/girara/

# zlib
PERMIT_PACKAGE =Yes

WANTLIB += gdk-3 gio-2.0 glib-2.0 gobject-2.0 gtk-3 intl json-glib-1.0
WANTLIB += m pango-1.0

SITES =		https://pwmt.org/projects/girara/download/
MODULES =	devel/meson

BUILD_DEPENDS =	devel/gettext,-tools
LIB_DEPENDS =	x11/gtk+3 \
		devel/json-glib

CONFIGURE_ARGS +=	-Ddocs=disabled \
			-Dtests=disabled

# c11
COMPILER =	base-clang ports-gcc
COMPILER_LANGS =	c

# tests now need xvfb-run
NO_TEST =	Yes
#TEST_TARGET =	test
#TEST_FLAGS +=	VERBOSE=1
#TEST_FLAGS +=	HOME=${WRKDIR}
#TEST_IS_INTERACTIVE =X11

.include <bsd.port.mk>
