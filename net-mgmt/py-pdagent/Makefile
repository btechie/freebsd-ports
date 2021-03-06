# Created by: Mark Felder <feld@FreeBSD.org>
# $FreeBSD$

PORTNAME=	pdagent
PORTVERSION=	1.4
DISTVERSIONPREFIX=v
PORTREVISION=	2
CATEGORIES=	net-mgmt python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	PagerDuty Agent software

LICENSE=	BSD3CLAUSE

USES=		python:2.7 shebangfix
USE_PYTHON=	flavors
SHEBANG_FILES=	bin/*
NO_ARCH=	yes
NO_BUILD=	yes

USE_RC_SUBR=	pdagentd

USE_GITHUB=	YES
GH_ACCOUNT=	PagerDuty

SUB_LIST+=	PYTHON_CMD="${PYTHON_CMD}"

BINFILES=	pd-queue pd-send pdagentd.py

USERS=	pdagent
GROUPS=	pdagent

do-patch:
	${REINPLACE_CMD} -e 's|/var/lib/pdagent|/var/db/pdagent|' -e 's|/etc|${ETCDIR}|' ${WRKSRC}/pdagent/confdirs.py

do-install:
	${MKDIR} ${STAGEDIR}${PYTHON_SITELIBDIR} ${STAGEDIR}/${ETCDIR}
	(cd ${WRKSRC} && ${COPYTREE_SHARE} pdagent ${STAGEDIR}${PYTHON_SITELIBDIR})
.for i in ${BINFILES}
	${INSTALL_SCRIPT} ${WRKSRC}/bin/${i} ${STAGEDIR}/${PREFIX}/bin/${i}
.endfor
	${INSTALL_DATA} ${WRKSRC}/conf/pdagent.conf ${STAGEDIR}/${ETCDIR}/pdagent.conf.sample

.include <bsd.port.mk>
