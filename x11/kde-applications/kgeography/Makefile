COMMENT =	geography learning tool for KDE
DISTNAME =	kgeography-${VERSION}
CATEGORIES =	geo

WANTLIB += ${COMPILER_LIBCXX} GL KF6ColorScheme KF6ConfigCore
WANTLIB += KF6ConfigGui KF6ConfigWidgets KF6CoreAddons KF6Crash
WANTLIB += KF6GuiAddons KF6I18n KF6IconThemes KF6ItemViews KF6WidgetsAddons
WANTLIB += KF6XmlGui Qt6Core Qt6DBus Qt6Gui Qt6Widgets Qt6Xml
WANTLIB += c m

MODKDE_DESKTOP_FILE = yes
MODKDE_ICON_CACHE = yes
MODKDE_TRANSLATIONS = yes
MODKF5_I18N_CONFLICT = yes
MODKF5_L10N_CONFLICT = yes
MODKDE_DOCS = yes

LIB_DEPENDS =	devel/kf6/kcolorscheme \
		devel/kf6/kconfig \
		devel/kf6/kconfigwidgets \
		devel/kf6/kcoreaddons \
		devel/kf6/kcrash \
		devel/kf6/kguiaddons \
		devel/kf6/ki18n \
		devel/kf6/kiconthemes \
		devel/kf6/kitemviews \
		devel/kf6/kwidgetsaddons \
		devel/kf6/kxmlgui

.include <bsd.port.mk>
