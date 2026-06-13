FROM maven AS buildstage
RUN mkdir /opt/AWS-Linux 
WORKDIR /opt/AWS-Linux
COPY . .
RUN mvn clean install  


FROM tomcat
WORKDIR webapps
COPY --from=buildstage /opt/AWS-Linux/target/*.war .
RUN rm -rf ROOT && \
    mv *.war  ROOT.war
EXPOSE 8080
