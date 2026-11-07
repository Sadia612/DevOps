# Lab 5: Build, Test, and Package Applications

**GitHub username:** sadia612

## Tasks done

1. **IntelliJ in Docker:** cloned the setup repo, ran `setup.sh`, opened IntelliJ at port 3001.
2. **Maven (java-maven-app):** installed Maven, ran `mvn package`, added Elasticsearch 7.0.0, ran `mvn test` and the JAR.
3. **Gradle (java-app):** used JDK 16, ran `./gradlew build`, added Elasticsearch 7.0.0, rebuilt and ran the JAR.
4. **Node.js (node-project):** ran `npm install`, `npm start` (port changed to 4000), `npm test` and `npm pack`.
5. **React API (react-nodejs-example):** ran `npm install` and `npm run build` in `api`, viewed `server.bundle.js`.
6. **Docker:** built the image `lab5:1.0` from the Dockerfile.

## Practice answers

1. The JAR name comes from `artifactId` and `version` in `pom.xml`. The package phase compiles, tests and packs the code into a JAR in `target`.
2. `./gradlew` downloads its own Gradle version. For Java version errors, check Project SDK, Gradle JVM and `JAVA_HOME`.
3. Port 3000 is already used by the IntelliJ desktop in the container, so the app uses port 4000.

## Files

Screenshots are in the `screenshots` folder. The report is in `Lab5_Solution.pdf`.
