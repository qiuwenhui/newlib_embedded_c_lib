#	from: @(#)Makefile	2.3 88/08/11 4.0 RPCSRC
#	$FreeBSD: src/include/rpc/Makefile,v 1.1 2001/03/19 12:49:46 alfred Exp $

.SUFFIXES: .x

RPCCOM = rpcgen -C

HDRS=	rpcb_prot.h

XFILES= rpcb_prot.x

HFILES=	auth.h auth_unix.h clnt.h clnt_soc.h clnt_stat.h \
	nettype.h pmap_clnt.h pmap_prot.h pmap_rmt.h raw.h \
	rpc.h rpc_msg.h rpcb_clnt.h rpcent.h rpc_com.h \
	svc.h svc_auth.h svc_soc.h svc_dg.h types.h xdr.h

# Secure RPC
HFILES+= auth_des.h des.h des_crypt.h

# Kerberos
HFILES+= auth_kerb.h

CLEANFILES+= ${HDRS}

all: ${HDRS}

beforeinstall:
	${INSTALL} -C -o ${BINOWN} -g ${BINGRP} -m 444 \
		${HFILES:S;^;${.CURDIR}/;} \
		${XFILES:S;^;${.CURDIR}/;} \
		${HDRS} \
		${DESTDIR}/usr/include/rpc

.x.h:
	${RPCCOM} -h -DWANT_NFS3 ${.IMPSRC} -o ${.TARGET}

.include <bsd.prog.mk>
