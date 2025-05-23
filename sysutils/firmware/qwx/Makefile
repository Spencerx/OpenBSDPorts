FW_DRIVER=	qwx

FW_VER=		20240909
REVISION=	0

DISTNAME=	linux-firmware-${FW_VER}
EXTRACT_SUFX=	.tar.xz
# broad enough to reduce WRKSRC size but specific enough to match all DISTFILES
EXTRACT_FILES=	\*/{ath11k\*,LICEN\*,WHENCE}

SITES=		https://cdn.kernel.org/pub/linux/kernel/firmware/
HOMEPAGE=	https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath11k

# can be redistributed, but shouldn't be in normal packages directory as
# this is only meant for use with fw_update.
PERMIT_PACKAGE=	  firmware
PERMIT_DISTFILES= Yes

FW=	QCA2066/hw2.1 \
	WCN6855/hw2.0

do-install:
	# As referenced by the WHENCE file
	${INSTALL_DATA} ${WRKSRC}/LICENSE.QualcommAtheros_ath10k \
	    ${PREFIX}/firmware/qwx-license
.for device in ${FW}
. for i in amss board-2 m3
	${INSTALL_DATA} ${WRKSRC}/ath11k/${device}/${i}.bin \
	    ${PREFIX}/firmware/qwx-${device:L:S/\//-/g}-${i}
.  endfor
.  if "${device}" == "WCN6855/hw2.0"
	${INSTALL_DATA} ${WRKSRC}/ath11k/${device}/regdb.bin \
	    ${PREFIX}/firmware/qwx-${device:L:S/\//-/g}-regdb

	# XXX - This hardware rev does not have separate files
.   for i in amss board-2 m3 regdb
	cd ${PREFIX}/firmware && \
	    ln qwx-wcn6855-hw2.0-${i} qwx-wcn6855-hw2.1-${i}
.   endfor
.  endif
.endfor

.include <bsd.port.mk>
