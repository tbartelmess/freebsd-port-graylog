# Created by: Thomas Bartelmess <thomas@bartelmess.io>
# $FreeBSD$

PORTNAME=	graylog
PORTVERSION=	2.2.2
CATEGORIES=	sysutils java
MASTER_SITES=	https://packages.graylog2.org/releases/graylog/ \
		http://packages.graylog2.org/releases/graylog/

MAINTAINER=	thomas@bartelmess.io
COMMENT=	Tool for centralized log collection

LICENSE=	GPLv3+

USES=		tar:tgz
USE_JAVA=	yes
JAVA_VERSION=	1.7+
JAVA_EXTRACT=	yes
NO_ARCH=	yes
JAVA_RUN=	yes
NO_BUILD=	yes

USE_RC_SUBR=	graylog
SUB_FILES=	server.conf.sample pkg-message

GRAYLOGUSER?=	graylog
GRAYLOGGROUP?=	${GRAYLOGUSER}
USERS=		${GRAYLOGUSER}
GROUPS=		${GRAYLOGGROUP}
GRAYLOG_DATA_DIR=	/var/db/graylog

SUB_LIST=	GRAYLOGUSER=${GRAYLOGUSER} \
		GRAYLOGGROUP=${GRAYLOGGROUP} \
		GRAYLOG_DATA_DIR=${GRAYLOG_DATA_DIR}

PLIST_SUB=	GRAYLOG_DATA_DIR=${GRAYLOG_DATA_DIR} \
		GRAYLOGUSER=${GRAYLOGUSER} \
		GRAYLOGGROUP=${GRAYLOGGROUP}

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}/plugin
	${MKDIR} ${STAGEDIR}${ETCDIR}/server
	${MKDIR} ${STAGEDIR}${GRAYLOG_DATA_DIR}
	${INSTALL_DATA} ${WRKSRC}/graylog.jar ${STAGEDIR}${DATADIR}
	(cd ${WRKSRC}/plugin && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/plugin)
	${INSTALL_DATA} ${WRKDIR}/server.conf.sample ${STAGEDIR}${ETCDIR}/server/server.conf.sample

.include <bsd.port.mk>
