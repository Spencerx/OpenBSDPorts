COMMENT=		companion library to GObject and Gtk+

GNOME_PROJECT=		libdazzle
GNOME_VERSION=		3.44.0
REVISION=		2

SHARED_LIBS += dazzle-1.0                1.2 # 0

CATEGORIES=		devel

# GPLv3
PERMIT_PACKAGE=		Yes

WANTLIB += c cairo gdk-3 gdk_pixbuf-2.0 gio-2.0 glib-2.0 gobject-2.0
WANTLIB += gtk-3 intl m pango-1.0

# -std=gnu11
COMPILER=		base-clang ports-gcc
COMPILER_LANGS=		c

MODULES=		devel/meson \
			x11/gnome

MODGNOME_TOOLS=		gobject-introspection vala

LIB_DEPENDS=		x11/gtk+3

TEST_IS_INTERACTIVE=	x11

DEBUG_PACKAGES=		${BUILD_PACKAGES}

.include <bsd.port.mk>
