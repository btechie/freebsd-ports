# Created by: Christoph Kick
# $FreeBSD$

PORTNAME=	ffi
PORTVERSION=	1.9.25
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Extension for dynamic libraries & binding functions

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libffi.so:devel/libffi

USE_RUBY=	yes
USES=		gem

post-patch:
	@${LN} -s i386-freebsd ${WRKSRC}/lib/ffi/platform/arm-freebsd
	@${LN} -s x86_64-freebsd ${WRKSRC}/lib/ffi/platform/aarch64-freebsd

.include <bsd.port.mk>
