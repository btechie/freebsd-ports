# Created by: Denis Pokataev <catone@cpan.org>
# $FreeBSD$

PORTNAME=	pootle
PORTVERSION=	2.5.1.3
PORTREVISION=	3
CATEGORIES=	textproc
MASTER_SITES=	CHEESESHOP
DISTNAME=	Pootle-${PORTVERSION}

MAINTAINER=	rene@FreeBSD.org
COMMENT=	User-friendly web portal for simple translation process

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	translate-toolkit>=1.11.0:textproc/translate-toolkit \
		${PYTHON_PKGNAMEPREFIX}argparse>=0:devel/py-argparse@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}cssmin>=0.1.4:www/py-cssmin@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}south>=0.7.6:databases/py-south@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}lxml>=2.1.4:devel/py-lxml@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}django-assets>=0.8:www/py-django-assets@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}django-taggit>0.10:www/py-django-taggit@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}django-voting>=0.1:www/py-django-voting@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}south>=0.7.6:databases/py-south@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}diff-match-patch>=0:textproc/py-diff-match-patch@${PY_FLAVOR}
# actually diff-match-patch is a dependency of translate-toolkit,
# but only this port uses it.

NO_ARCH=	yes
USES=		gettext python:2.7 tar:bzip2 shebangfix
USE_PYTHON=	autoplist distutils
SHEBANG_FILES=	pootle/assets/admin/js/compress.py

USERS=		pootle
GROUPS=		pootle

PLIST_SUB+=	POOTLEUSER="${USERS}" \
		POOTLEGROUP="${GROUPS}"

USE_RC_SUBR=	pootle
SUB_LIST+=	PYTHON_CMD="${PYTHON_CMD}"

PORTDOCS=	CREDITS INSTALL LICENSE

OPTIONS_DEFINE=	DOCS LDAP MEMCACHED
OPTIONS_GROUP=	DB
DB_DESC=	Database backend
OPTIONS_GROUP_DB=MYSQL PGSQL
OPTIONS_DEFAULT=MEMCACHED MYSQL

MEMCACHED_DESC=	Use memcached to improve performance

LDAP_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}ldap2>0:devel/py-ldap2@${PY_FLAVOR}

MEMCACHED_LIB_DEPENDS=	libmemcached.so:databases/libmemcached
MEMCACHED_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}python-memcached>=1.45:databases/py-python-memcached@${PY_FLAVOR}

MYSQL_USES=		mysql:client
MYSQL_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}MySQLdb>0:databases/py-MySQLdb@${PY_FLAVOR}

PGSQL_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}psycopg2>0:databases/py-psycopg2@${PY_FLAVOR}

pre-configure:
	@${REINPLACE_CMD} -e "s/,<0.11.2//g" \
		-e "s/,<0.8//g" \
		-e "s/==0.1//g" \
		-e "s/,<1.5//g" \
		${WRKSRC}/requirements/base.txt

post-install-DOCS-on:
	${MKDIR} ${STAGEDIR}/${DOCSDIR}
.for docs in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${docs} ${STAGEDIR}/${DOCSDIR}
.endfor

.include <bsd.port.mk>
