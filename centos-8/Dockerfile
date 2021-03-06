#template dockerfile to build a centos-based build image
# run with "docker build --rm -t farm-centos-XXX Dockerfile.centos"

FROM centos:centos8
MAINTAINER "Francesco Chemolli <kinkie@squid-cache.org>"
ADD local/* /usr/local/bin/
RUN \
	dnf update -y && \
	dnf install -y epel-release && \
	dnf --enablerepo=PowerTools install -y \
		autoconf \
		automake \
		bzip2 \
		ccache \
		clang \
		cppunit \
		cppunit-devel \
		curl \
		ed \
		expat-devel \
		git \
		gnutls-devel \
		gnutls-utils \
		libatomic \
		libatomic-static \
		libcap \
		libcap-devel \
		libdb-devel \
		libtdb \
		libtdb-devel \
		libtool \
		libtool-ltdl-devel \
		libxml2 \
		libxml2-devel \
		make \
		nettle-devel \
		openldap-devel \
		openssl-devel \
		pam-devel \
		perl-Perl-MinimumVersion \
		redhat-lsb-core \
		screen \
		vim \
		xz \
	&& \
	dnf clean all && \
	rm -f /etc/profile.d/ccache* && \
	true
RUN \
	groupadd -g 1000 jenkins && \
	useradd -u 1000 -m -g jenkins -G ccache jenkins && \
	groupadd -g 1001 kinkie && \
	useradd -u 1001 -m -g kinkie -G ccache kinkie && \
	true

USER jenkins
CMD ["/bin/bash", "-l"]
