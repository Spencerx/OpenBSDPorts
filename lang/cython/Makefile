COMMENT=	optimising static compiler for Python and Cython

MODPY_DISTV=	3.0.12
REVISION=	0
DISTNAME=	cython-${MODPY_DISTV}
PKGNAME=	py-cython-${MODPY_DISTV}
CATEGORIES=	lang

EPOCH=		0

HOMEPAGE=	https://cython.org/

# Apache 2
PERMIT_PACKAGE=	Yes

WANTLIB += pthread ${MODPY_WANTLIB}

MODULES=	lang/python
MODPY_PYBUILD=	setuptools
MODPY_PI=	Yes

TEST_DEPENDS=	math/py-numpy

PORTHOME=	${WRKDIR}
TEST_TARGET=	test

MAKE_ENV=	PYTHON=${MODPY_BIN}

do-test:
	@cd ${WRKBUILD} && ${SETENV} ${MAKE_ENV} TESTOPTS=-j${MAKE_JOBS} \
		${MAKE_PROGRAM} ${ALL_TEST_FLAGS} -f ${MAKE_FILE} ${TEST_TARGET}

.include <bsd.port.mk>
