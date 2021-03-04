
#A multistage build with two from instructions 
#Important process in this is to copy one image to another 
#What am i doing here? i'm taking java code, compiling and deploying in an JBOSS container 

FROM maven:3-jdk-7 AS app   
#name of image is app

WORKDIR /usr/src/movieplex7   
#workdir for image 

COPY pom.xml .    #copy the pom file

RUN mvn -B -f pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve  
 #executing runcommand 

COPY . .          
#copy all files from app to current container

RUN MVN -B -s /usr/share/maven/ref/settings-docker.xml package -DskipTests    
 #run command 

FROM jboss/wildfly  #final from is actual image going to be build

RUN /opt/jboss/wildfly/bin/add-user.sh admin Admin --silent 

COPY --from=app /usr/src/movieplex7/target/movieplex7-1.0-SNAPSHOT.war .      		

#going to copy from this app and copy the war file to this container (An image to image copy) 

EXPOSE 8080 9990       			
#expose to real world

CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]

