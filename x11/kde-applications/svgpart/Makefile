COMMENT =	KPart for viewing SVGs
DISTNAME =	svgpart-${VERSION}
PKGNAME =	kf6-svgpart-${VERSION}
CATEGORIES =	graphics

WANTLIB += ${COMPILER_LIBCXX} GL KF6ColorScheme KF6ConfigCore
WANTLIB += KF6ConfigGui KF6ConfigWidgets KF6CoreAddons KF6GuiAddons
WANTLIB += KF6I18n KF6KIOCore KF6Parts KF6WidgetsAddons KF6XmlGui
WANTLIB += Qt6Core Qt6DBus Qt6Gui Qt6Network Qt6Svg Qt6SvgWidgets
WANTLIB += Qt6Widgets Qt6Xml m

MODKDE_TRANSLATIONS = yes
MODKF5_L10N_CONFLICT = yes

LIB_DEPENDS =	devel/kf6/kconfig \
		devel/kf6/kcolorscheme \
		devel/kf6/kconfigwidgets \
		devel/kf6/kcoreaddons \
		devel/kf6/kcoreaddons \
		devel/kf6/ki18n \
		devel/kf6/kio \
		devel/kf6/kguiaddons \
		devel/kf6/kparts \
		devel/kf6/kwidgetsaddons \
		devel/kf6/kxmlgui \
		x11/qt6/qtsvg

.include <bsd.port.mk>
