# Created by: Piotr Kubaj <pkubaj@anongoth.pl>
# $FreeBSD$

PORTNAME=	tcl
PORTVERSION=	8.5.13
PORTREVISION=	1
CATEGORIES=	lang linux
PKGNAMESUFFIX=	85

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Tool Command Language (Linux CentOS ${LINUX_DIST_VER})

CONFLICTS=	linux-c6-${PORTNAME}${PKGNAMESUFFIX}-[0-9]*

DATADIR=	${PREFIX}/usr/share/tcl${PORTVERSION:R}
DESCR=		${.CURDIR}/../${PORTNAME}${PKGNAMESUFFIX}/pkg-descr
RPMVERSION=	8.el7
USES=		linux:c7
USE_LDCONFIG=	yes
USE_LINUX_RPM=	yes
USE_LINUX_RPM_BAD_PERMS=	yes

OPTIONS_DEFINE=	DOCS

.include <bsd.port.mk>
