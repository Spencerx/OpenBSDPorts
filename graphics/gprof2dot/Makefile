COMMENT=	convert profilers output into a dot(1) graph

GH_ACCOUNT=	jrfonseca
GH_PROJECT=	gprof2dot
GH_TAGNAME=	2024.06.06
MODPY_DISTV=	${GH_TAGNAME:C/\.0/./g}
REVISION=	0

CATEGORIES=	graphics

# LGPLv3+
PERMIT_PACKAGE=	Yes

MODULES=	lang/python
MODPY_PYBUILD=	setuptools
RUN_DEPENDS=	math/graphviz

do-test:
	${MODPY_BIN} ${WRKSRC}/tests/test.py

.include <bsd.port.mk>
