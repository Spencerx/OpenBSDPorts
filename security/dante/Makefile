COMMENT=	SOCKS client and server

DISTNAME=	dante-1.4.4

CATEGORIES=	security

SHARED_LIBS=	dsocks	1.4 \
		socks	1.4
MODGNU_SHARED_LIBS=dsocks	'-export-dynamic' \
		socks		''

HOMEPAGE=	https://www.inet.no/dante/

SITES=		${HOMEPAGE}/files/

# BSD/CMU
PERMIT_PACKAGE=	Yes

WANTLIB=	c m

CONFIGURE_STYLE= gnu
CONFIGURE_ARGS+= --enable-static
CONFIGURE_ARGS+= --without-gssapi \
		--without-krb5 \
		--without-ldap \
		--without-libwrap \
		--without-pam \
		--without-sasl \
		--without-upnp

pre-configure:
	${SUBST_CMD} ${WRKSRC}/bin/socksify.in

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/dante
	${INSTALL_DATA} ${WRKSRC}/doc/README.* ${PREFIX}/share/doc/dante
	${INSTALL_DATA} ${WRKSRC}/doc/SOCKS4.* ${PREFIX}/share/doc/dante
	${INSTALL_DATA} ${WRKSRC}/doc/rfc* ${PREFIX}/share/doc/dante
	${INSTALL_DATA_DIR} ${PREFIX}/share/examples/dante
	${INSTALL_DATA} ${WRKSRC}/example/*.conf ${PREFIX}/share/examples/dante

.include <bsd.port.mk>
