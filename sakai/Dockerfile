FROM ubuntu:xenial

LABEL maintainer="damien.cupif@nist.gov"

# Prepare the target directory for deployment
ENV TARGET_DIR=/sakai-target
RUN mkdir $TARGET_DIR

# Add the add-apt-repository tool
RUN apt-get update && apt-get install -y software-properties-common

# Install JAVA 8 oracle
RUN add-apt-repository ppa:webupd8team/java
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections
RUN apt-get update && apt-get install -y \
	oracle-java8-installer

# Install other dependencies
RUN apt-get update && apt-get install -y \
	git \
	maven \
	&& apt-get clean

# Install Sakai
RUN git clone https://github.com/sakaiproject/sakai.git /sakai
WORKDIR /sakai
RUN git checkout 11.2
RUN mvn clean install sakai:deploy -Dmaven.tomcat.home=$TARGET_DIR -Dmaven.test.skip=true