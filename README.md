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


2. Apply .gitignore
git rm -r --cached .
git add .
git commit -m ".gitignore is now working"


3. nginx.conf

events {}

http {
	server {
	    listen 80;
		
		location / {
			proxy_pass http://localhost:3000;
			proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
		}
	  
	    location /api {
			proxy_pass http://localhost:8080/api;
			proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
		}
	  
	}
}

