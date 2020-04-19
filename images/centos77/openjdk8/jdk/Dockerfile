FROM centos:7.7.1908
LABEL maintainer="massimo.groppelli@zucchetti.it"

# ###########
# VI EDITOR #
# ###########
# Turn on color syntax highlighting and display line numbers along the left side of a window
RUN echo "syntax on" > ~/.vimrc \
	&& echo "set number" >> ~/.vimrc
# When you are inserting text, if you press Enter at the end of your text, 
# vi will automatically indent the next new line to match the indent of the previous one.
# Each indentation level is four spaces and tabs are not used. (Popular with Java programmers)
RUN echo "set autoindent" >> ~/.vimrc \
	&& echo "set softtabstop=4" >> ~/.vimrc \
	&& echo "set shiftwidth=4" >> ~/.vimrc \
	&& echo "set expandtab" >> ~/.vimrc
# Install file utility
RUN yum -y install file

# ##########
# OPEN JDK #
# ##########
# /dev/urandom is used as random source, which is prefectly safe
# according to http://www.2uo.de/myths-about-urandom/
RUN yum install -y \
       java-1.8.0-openjdk-1.8.0.242.b08-0.el7_7 \
       java-1.8.0-openjdk-devel-1.8.0.242.b08-0.el7_7 \ 
    && echo "securerandom.source=file:/dev/urandom" >> /usr/lib/jvm/jre/lib/security/java.security \
    && yum clean all
ENV JAVA_MAJOR_VERSION=8
ENV JAVA_HOME /etc/alternatives/jre