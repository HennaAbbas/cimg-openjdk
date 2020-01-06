# vim:set ft=dockerfile:

FROM cimg/base:2019.10

LABEL maintainer="CircleCI Community & Partner Engineering Team <community-partner@circleci.com>"

# This can be removed with the next monthly base image.
# Generate & set locale
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

ENV JAVA_VERSION 11.0.2
ENV URL https://download.java.net/java/GA/jdk11/9/GPL/openjdk-11.0.2_linux-x64_bin.tar.gz

RUN curl -o java.tar.gz "${URL}" && \
	tar -xzf java.tar.gz -C /usr/local && \
	rm java.tar.gz && \
	ln -s /usr/local/jdk-${JAVA_VERSION}/bin/java /usr/bin/java && \
	ln -s /usr/local/jdk-${JAVA_VERSION}/bin/javac /usr/bin/javac && \
	ln -s /usr/local/jdk-${JAVA_VERSION}/bin/javaws /usr/bin/javaws && \

	# Simple smoke tests
	/usr/bin/java --version && \
	/usr/bin/javac --version 
	
ENV JAVA_HOME /usr/local/jdk-${JAVA_VERSION}
	
WORKDIR /root/project