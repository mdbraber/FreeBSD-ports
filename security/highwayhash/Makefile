# Created by: Yuri Victorovich <yuri@rawbw.com>
# $FreeBSD$

PORTNAME=	highwayhash
PORTVERSION=	g20181002
PORTREVISION=	1
CATEGORIES=	security

MAINTAINER=	yuri@FreeBSD.org
COMMENT=	Fast strong hash functions: SipHash/HighwayHash

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

BROKEN_aarch64=		fails to compile: /usr/lib/clang/5.0.0/include/mmintrin.h:47:5: use of undeclared identifier '__builtin_ia32_emms'
BROKEN_powerpc64=	fails to compile: g++6: error: unrecognized command line option '-mavx2'
ONLY_FOR_ARCHS=		aarch64 amd64 powerpc powerpc64
ONLY_FOR_ARCHS_REASON=	Assembly is implemented only for specific architectures in highwayhash/tsc_timer.h

USES=		compiler:c++11-lib gmake
USE_GITHUB=	yes
GH_ACCOUNT=	google
GH_TAGNAME=	c5ee50b
USE_LDCONFIG=	yes

# workaround for https://github.com/google/highwayhash/issues/69

post-install:
	# Symlink upstream issue: https://github.com/google/highwayhash/issues/57
	${RM} ${STAGEDIR}${PREFIX}/lib/libhighwayhash.so
	${LN} -s libhighwayhash.so.0 ${STAGEDIR}${PREFIX}/lib/libhighwayhash.so

.include <bsd.port.mk>
