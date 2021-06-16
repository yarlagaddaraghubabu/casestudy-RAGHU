FROM centos
                   RUN mkdir /opt/tomcat/
                  WORKDIR /opt/tomcat
                  RUN yum -y install java
                  RUN java -version
                  RUN curl -O https://downloads.apache.org/tomcat/tomcat-8/v8.5.59/bin/apache-tomcat-8.5.59.tar.gz
                  RUN tar xvfz apache*.tar.gz
                  RUN mv apache-tomcat-8.5.59/* /opt/tomcat/.
                  #https://tomcat.apache.org/tomcat-8.0-doc/appdev/sample/
                  COPY ./sample.war /opt/tomcat/webapps
                  EXPOSE 8080
                  CMD ["/opt/tomcat/bin/catalina.sh", "run"] 

