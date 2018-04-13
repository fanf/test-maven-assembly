
This repos demonstrate the fact that maven-assembly-plugin includes 
`provided` dependencies with the default "jar-with-dependencies" descriptor. 

This is discussed here: https://stackoverflow.com/questions/49784429/how-to-exclude-transitive-dependencies-with-scope-provided-with-maven-assembly-p

And a bug report is here: https://issues.apache.org/jira/browse/MASSEMBLY-883

Testing
-------

```
git clone https://github.com/fanf/test-maven-assembly.git
cd test-maven-assembly
mvn package
jar -tf target/test-1.0-SNAPSHOT-jar-with-dependencies.jar | grep slf4j
```

Will result in: 

```
org/slf4j/
org/slf4j/event/
org/slf4j/helpers/
org/slf4j/spi/
META-INF/maven/org.slf4j/
META-INF/maven/org.slf4j/slf4j-api/
org/slf4j/event/EventConstants.class
org/slf4j/event/EventRecodingLogger.class
....
```
