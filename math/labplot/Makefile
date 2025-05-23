COMMENT =	data visualization and analysis software

DISTNAME =	labplot-2.12.0

CATEGORIES =	math x11

HOMEPAGE =	https://labplot.kde.org/

MAINTAINER =	Rafael Sadowski <rsadowski@openbsd.org>

# luajit (via cantorlibs)
USE_NOBTCFI =	Yes
USE_NOBTCFI-aarch64 =	Yes# fortran

SHARED_LIBS +=	labplot                   0.0 # 0.0

# LGPL, GPL and many others
PERMIT_PACKAGE =	Yes

WANTLIB += ${COMPILER_LIBCXX} GL KF6Archive KF6Attica KF6Bookmarks
WANTLIB += KF6ColorScheme KF6Completion KF6ConfigCore KF6ConfigGui
WANTLIB += KF6ConfigWidgets KF6CoreAddons KF6Crash KF6GuiAddons
WANTLIB += KF6I18n KF6IconThemes KF6ItemViews KF6JobWidgets KF6KIOCore
WANTLIB += KF6KIOFileWidgets KF6KIOGui KF6KIOWidgets KF6NewStuffCore
WANTLIB += KF6NewStuffWidgets KF6Parts KF6Purpose KF6PurposeWidgets
WANTLIB += KF6Service KF6Solid KF6SonnetUi KF6SyntaxHighlighting
WANTLIB += KF6TextWidgets KF6UserFeedbackCore KF6UserFeedbackWidgets
WANTLIB += KF6WidgetsAddons KF6XmlGui QXlsxQt6 Qt6Core Qt6DBus
WANTLIB += Qt6Gui Qt6Network Qt6PrintSupport Qt6SerialPort Qt6Sql
WANTLIB += Qt6Svg Qt6Widgets Qt6Xml c cantorlibs cerf cfitsio
WANTLIB += fftw3 gsl gslcblas hdf5 lz4 m markdown matio netcdf
WANTLIB += poppler poppler-qt6 qt6advanceddocking spectre xcb
WANTLIB += z zstd

SITES =		https://download.kde.org/stable/labplot/
EXTRACT_SUFX =	.tar.xz

MODULES =	devel/kf6

RUN_DEPENDS =	devel/desktop-file-utils \
		devel/gettext,-tools \
		misc/shared-mime-info \
		math/eigen3 \
		x11/gtk+4,-guic

BUILD_DEPENDS =	devel/bison \
		math/eigen3 \
		devel/desktop-file-utils \
		misc/shared-mime-info \
		devel/kf6/knewstuff \
		devel/gettext,-tools \
		devel/kf6/kdoctools

LIB_DEPENDS =	archivers/lz4 \
		archivers/zstd \
		devel/gsl \
		devel/kf6/attica \
		devel/kf6/karchive \
		devel/kf6/kbookmarks \
		devel/kf6/kcolorscheme \
		devel/kf6/kcompletion \
		devel/kf6/kconfig \
		devel/kf6/kconfigwidgets \
		devel/kf6/kcoreaddons \
		devel/kf6/kcrash \
		devel/kf6/kguiaddons \
		devel/kf6/ki18n \
		devel/kf6/kiconthemes \
		devel/kf6/kio \
		devel/kf6/kitemviews \
		devel/kf6/kjobwidgets \
		devel/kf6/knewstuff \
		devel/kf6/kparts \
		devel/kf6/kservice \
		devel/kf6/ktextwidgets \
		devel/kf6/kuserfeedback \
		devel/kf6/kwidgetsaddons \
		devel/kf6/kxmlgui \
		devel/kf6/purpose \
		devel/kf6/solid \
		devel/kf6/sonnet \
		math/cfitsio \
		math/fftw3,-main,double \
		print/libspectre \
		print/poppler,-qt6 \
		textproc/discount \
		x11/kde-applications/cantor \
		x11/qt6/qtserialport \
		x11/qt6/qtsvg \
		x11/qtadvanceddocking

# OPTIONAL packages
LIB_DEPENDS +=	devel/kf6/syntax-highlighting \
		math/hdf5 \
		math/libcerf \
		math/matio \
		math/netcdf \
		textproc/qxlsx

#-- The following OPTIONAL packages have not been found:
#* LibOrigin, A library for reading OriginLab project files,
#  <https://sourceforge.net/projects/liborigin>
#* Qt5Mqtt, Qt Module to implement MQTT protocol version 3.1 and 3.1.1,
# <https://github.com/qt/qtmqtt>
#* ReadStat, A command-line tool and library for reading files from
# popular stats packages, <https://github.com/WizardMac/ReadStat>
CONFIGURE_ARGS =	-DENABLE_READSTAT=OFF
CONFIGURE_ARGS +=	-DENABLE_MQTT=OFF
CONFIGURE_ARGS +=	-DENABLE_LIBORIGIN=OFF

CONFIGURE_ARGS +=	-DKDE_INSTALL_MANDIR=${WRKINST}/man

CONFIGURE_ARGS +=	-DCMAKE_DISABLE_FIND_PACKAGE_Git=On

CONFIGURE_ARGS +=	-DENABLE_VECTOR_BLF=OFF

CONFIGURE_ARGS +=	-DCMAKE_MODULE_PATH=${LOCALBASE}/lib/cmake

CONFIGURE_ARGS +=	-DQT_VERSION_MAJOR=6

MODCMAKE_LDFLAGS =	-L${X11BASE}/lib -L${LOCALBASE}/lib

TEST_IS_INTERACTIVE =	X11

pre-configure:
	# use system dependencies
	rm -rf ${WRKSRC}/src/3rdparty/{cmake,kdmactouchbar,liborigin,QXlsx}

.include <bsd.port.mk>
