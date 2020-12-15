# jacoco-agent-docker

Image containing the jacoco javaagent to use as a volume container.

# Usage (docker-compose example jboss/wildfly)

```yaml
version: '3.8'
services:
  jacoco:
    image: devatypic/jacoco-agent-docker:0.8.6
  www:
    environment:
      JAVA_TOOL_OPTIONS: -javaagent:/jacoco/lib/jacocoagent.jar=excludes=*_javassit_*:javax.xml.soap.*:oasis.*,output=tcpserver,address=*
    image: jboss/wildfly
    volumes:
      - type: bind
        source: ./jacoco
        target: /jacoco
volumes:
  jacoco:

```

# Usage (docker-compose example payara/server-full)
```yaml
version: '3.8'
services:
  jacoco:
    image: devatypic/jacoco-agent-docker:0.8.6
  www:
    environment:
      JVM_ARGS: -javaagent:/jacoco/lib/jacocoagent.jar=excludes=*_javassit_*:javax.xml.soap.*:oasis.*,output=tcpserver,address=*
    image: payara/server-full:5.2020.6-jdk11
    volumes:
      - type: bind
        source: ./jacoco
        target: /jacoco
volumes:
  jacoco:

```

#  Usage (docker-compose example payara/server-full from Dockerfile)
```yaml
version: '3.8'
services:
  jacoco:
    image: devatypic/jacoco-agent-docker:0.8.6
  www:
    environment:
      JVM_ARGS: -javaagent:/jacoco/lib/jacocoagent.jar=excludes=*_javassit_*:javax.xml.soap.*:oasis.*,output=tcpserver,address=*
    build: .
    volumes:
      - type: bind
        source: ./jacoco
        target: /jacoco
volumes:
  jacoco:

```
