#template dockerfile to build a centos-based build image
# run with "docker build --rm -t farm-centos-XXX Dockerfile.centos"

ARG distro=debian
ARG version=unstable
FROM ${distro}:${version}
MAINTAINER "Francesco Chemolli <kinkie@squid-cache.org>"
ADD local/* /usr/local/bin/
RUN \
	apt-get update && \
	apt-get upgrade --no-install-recommends -y && \
	apt-get install --no-install-recommends -y \
		autoconf \
		autoconf-archive \
		automake \
		bzip2 \
		ccache \
		clang \
		curl \
		default-jre-headless \
		ed \
		g++ \
		g++-mingw-w64 \
		groff \
		git \
		gnutls-bin \
		libcap-dev \
		libcppunit-dev \
		libexpat-dev \
		libgnutls28-dev \
		libltdl-dev \
		libssl-dev \
		libtdb-dev \
		libtool \
		libtool-bin \
		libxml2-dev \
		linuxdoc-tools \
		lsb-release \
		make \
		nano \
		nettle-dev \
		pkg-config \
		po4a \
		translate-toolkit \
		xz-utils \
	&& \
	apt-get autoremove -y && \
	apt-get clean -y && \
	groupadd -g 1000 jenkins && \
	useradd -u 1000 -g jenkins -m jenkins && \
	groupadd -g 1001 kinkie && \
	useradd -u 1001 -m -g kinkie kinkie && \
	true

USER jenkins
CMD ["/bin/bash", "-l"]
