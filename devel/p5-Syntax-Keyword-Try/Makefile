COMMENT =	try/catch/finally syntax for perl

DISTNAME =	Syntax-Keyword-Try-0.30
REVISION =	0

CATEGORIES =	devel

MAINTAINER =		Alexander Bluhm <bluhm@openbsd.org>

# Perl
PERMIT_PACKAGE =	Yes

WANTLIB =		c perl

MODULES =		cpan

BUILD_DEPENDS =		devel/p5-XS-Parse-Keyword>=0.35
RUN_DEPENDS =		devel/p5-XS-Parse-Keyword>=0.35
TEST_DEPENDS =		devel/p5-Syntax-Keyword-Defer>=0.02

CONFIGURE_STYLE =	modbuild

MAKE_ENV =		TEST_POD=Yes

.include <bsd.port.mk>
