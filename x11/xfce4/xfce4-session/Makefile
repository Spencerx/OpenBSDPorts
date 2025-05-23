COMMENT=	Xfce4 session manager

XFCE_PROJECT=	xfce4-session
XFCE_VERSION=	4.20.2
REVISION=	0

# GPLv2
PERMIT_PACKAGE=	Yes

MODULES=	x11/xfce4
MODXFCE_DESKTOP_FILE=	Yes
MODXFCE_ICON_CACHE=	Yes
MODXFCE_PURGE_LA =	lib/xfce4/session/splash-engines

CONFIGURE_ENV=  ac_cv_header_sys_user_h=yes
CONFIGURE_ARGS=	--disable-linker-opts \
		--disable-systemd \
		--with-xsession-prefix=${PREFIX}
#CONFIGURE_ARGS+= --enable-session-screenshots
#XXX session-screenshots broken?
# http://bugzilla.xfce.org/show_bug.cgi?id=6885
LIB_DEPENDS=	x11/xfce4/libxfce4ui>=4.18.4 \
		x11/xfce4/libxfce4util>=4.19.2 \
		x11/xfce4/libxfce4windowing \
		x11/xfce4/xfconf>=4.12.0 \
		wayland/gtk-layer-shell \
		sysutils/polkit \
		devel/libwnck3

WANTLIB += ICE SM X11 X11-xcb XRes Xcomposite Xcursor Xdamage
WANTLIB += Xext Xfixes Xi Xinerama Xrandr Xrender fribidi
WANTLIB += atk-1.0 atspi c cairo dbus-1 expat ffi fontconfig
WANTLIB += freetype gdk_pixbuf-2.0 gio-2.0 glib-2.0
WANTLIB += gmodule-2.0 gobject-2.0 gthread-2.0 m pango-1.0
WANTLIB += pangocairo-1.0 pangoft2-1.0 pcre2-8 pixman-1 png pthread
WANTLIB += startup-notification-1 wnck-3 xcb xcb-util
WANTLIB += xcb-render xcb-shm xfce4ui-2 xfce4util xfconf-0 z
WANTLIB += harfbuzz graphite2 polkit-gobject-1 iconv intl
WANTLIB += atk-bridge-2.0 cairo-gobject epoxy gdk-3 gtk-3
WANTLIB += Xau Xdmcp display-info jpeg
WANTLIB += epoll-shim gtk-layer-shell wayland-client wayland-cursor
WANTLIB += wayland-egl xfce4windowing-0 xkbcommon
WANTLIB += ${COMPILER_LIBCXX}

FAKE_FLAGS=	settingsdir=${PREFIX}/share/examples/xfce4-session \
		conffilesdir=${PREFIX}/share/examples/xfce4-session \
		desktop_waylanddir=${PREFIX}/share/examples/xfce4-session

post-install:
	${SUBST_CMD} ${PREFIX}/bin/xflock4
	rm -f ${PREFIX}/bin/*.beforesubst

.include <bsd.port.mk>
