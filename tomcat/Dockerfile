FROM tomcat:8.0-jre8

LABEL maintainer="damien.cupif@nist.gov"

ENV CATALINA_HOME=/usr/local/tomcat
ENV JAVA_OPTS='-server -Xms512m -Xmx1024m -XX:PermSize=128m \
			-XX:NewSize=192m -XX:MaxNewSize=384m -Djava.awt.headless=true \
			-Dhttp.agent=Sakai -Dorg.apache.jasper.compiler.Parser.STRICT_QUOTE_ESCAPING=false \
			-Dsun.lang.ClassLoader.allowArraySyntax=true -Djava.util.Arrays.useLegacyMergeSort=true \
			-Dsakai.demo=true'

COPY ./context.xml $CATALINA_HOME/conf/context.xml
COPY ./server.xml $CATALINA_HOME/conf/server.xml
COPY ./catalina.properties $CATALINA_HOME/conf/catalina.properties

WORKDIR /tmp
RUN wget http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.36.tar.gz
RUN tar -zxvf mysql-connector-java-5.1.36.tar.gz
RUN mv mysql-connector-java-5.1.36/mysql-connector-java-5.1.36-bin.jar $CATALINA_HOME/lib/mysql-connector-java-5.1.36-bin.jar
