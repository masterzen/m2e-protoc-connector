# Lifecycle M2E connector for maven-protoc-plugin #

This is a m2e connector to be able to build Google Protobuf
Maven builds inside eclipse.

## Build ##


To build the plugin:

```
mvn package
```

This will both create the plugin jar and the eclipse feature.

It is necessary to use Maven 3, as Maven 2 can't build connectors.

## Installation ##

In Eclipse Indigo:

1. open the ``Install New Software`` window from the ``Help`` menu.
1. Then click on the ``Add`` button
1. select the ``Archive`` button and point it to the:
``com.daysofwonder.tools.m2e-protoc-connector.feature/target/com.daysofwonder.tools.m2e-protoc-connector.feature-1.0.0.20111130-1035-site.zip`` file.
1. Accept the license terms and restart eclipse. 

## Usage ##


Once installed, and if your project has already been imported, you must use M2E "Update Project Configuration"
to instruct eclipse and m2e to use the new connector.

You project POM should use the _maven-protoc-plugin_ like this:

```xml
	<plugin>
		<groupId>com.google.protobuf.tools</groupId>
		<artifactId>maven-protoc-plugin</artifactId>
		<executions>
			<execution>
				<id>generate proto sources</id>
				<goals>
					<goal>compile</goal>
				</goals>
				<phase>generate-sources</phase>
				<configuration>
					<protoSourceRoot>${basedir}/src/main/proto/</protoSourceRoot>
					<includes>
						<param>**/*.proto</param>
					</includes>
				</configuration>
			</execution>
		</executions>
	</plugin>
...
  <dependency>
  	<groupId>com.google.protobuf</groupId>
  	<artifactId>protobuf-java</artifactId>
  	<version>2.4.1</version>
  </dependency>
...
	<pluginRepositories>
		<pluginRepository>
			<id>dtrott-public</id>
			<name>David Trott's Public Repository</name>
			<url>http://maven.davidtrott.com/repository</url>
		</pluginRepository>
	</pluginRepositories>
```

#### Links

[blog article](http://www.masterzen.fr/2011/12/25/protobuf-maven-m2e-and-eclipse-are-on-a-boat/)
