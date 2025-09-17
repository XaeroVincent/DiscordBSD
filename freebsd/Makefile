PORTNAME=	discordbsd
CATEGORIES=	net-im

MAINTAINER=	tmp386@live.com
COMMENT=	An attempt at a native discord client for FreeBSD

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		electron:37 nodejs:22,build

USE_GITHUB=	yes
GH_ACCOUNT=	XaeroVincent
GH_PROJECT=	DiscordBSD
GH_TAGNAME=	main

SUB_FILES=	${PORTNAME}

USE_ELECTRON=	npm:npm prefetch extract rebuild:electron build:forge

PREFETCH_TIMESTAMP=
# ELECTRON_MAKE_FLAGS+=	--config electron-builder.yaml

pre-build:
	cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} npm run build
	${CP} ${WRKDIR}/${ELECTRON_DOWNLOAD_CACHE_DIR}/electron-v${UPSTREAM_ELECTRON_VER}-linux-${ELECTRON_ARCH}.zip \
		${WRKSRC}
do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME} ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
