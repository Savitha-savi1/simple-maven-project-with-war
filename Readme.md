# webhook-trigger update
# 
# Simple Maven WAR Project

## Structure

```
simple-war-app/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/HelloServlet.java
        └── webapp/
            ├── index.html
            └── WEB-INF/
                └── web.xml
```

## Build & Deploy

1. **Build WAR:**
   ```
   mvn clean package
   ```
   The WAR file will be generated in `target/simple-war-app-1.0-SNAPSHOT.war`.

2. **Deploy:**
   - Copy the WAR file to your Tomcat (or other servlet container) `webapps` directory.
   - Access: [http://localhost:8080/simple-war-app-1.0-SNAPSHOT/hello](http://localhost:8080/simple-war-app-1.0-SNAPSHOT/hello)
  
## Notes

- No Java code is strictly required for a static homepage. If you wish to add servlets or backend functionality, add Java classes under `src/main/java` and map them in `web.xml`.
test
