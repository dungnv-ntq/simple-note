# simple-note

1. run maven with active profile

+ add application profiles: application.properties, application-local.profiles, application-dev.profiles

+ add properties in file application.properties 
spring.profiles.active=@activatedProperties@

+ add profile_id in file pom.xml
<profiles>
	<profile>
		<id>dev</id>
		<properties>
			<activatedProperties>dev</activatedProperties>
		</properties>
	</profile>
	<profile>
		<id>local</id>
		<properties>
			<activatedProperties>local</activatedProperties>
		</properties>
		<activation>
			<activeByDefault>true</activeByDefault>
		</activation>
	</profile>
</profiles>

+ run with maven
- mvn spring-boot:run -P dev 
- mvn package -P dev
