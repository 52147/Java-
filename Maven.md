# Maven

## Traditional project
- jar pckages do not have the same version.
- Hard to maintain. For example, open Project that develop at linux environment at window environmenmt will appear some error.

## What is Maven
- Project management: 
  - Maven is a tool for managing the project based on the concept of project object model(POM).
  - One project is like a object.
  - Dependency management:Our project can be a resource for other use, and we can also use resource from others projects. 
  - Pom.xml: contains the information of one project.
- Build Lifecycle : 
  - process of POM -> Dependency
  - use many plugin to build the different goal. goal: jar package, source code, war, xml 
  - Process: pom.xml -> POM -> Dependency -> local repository -> remote repository -> Internet -> central repository
- Unified the development structure: Create a unified and standard project structure.

https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
https://www.bilibili.com/video/BV1Ah411S7ZE/?spm_id_from=333.337.search-card.all.click&vd_source=004e8f10a21c55becb57d8295b5ff681


## Maven
- mvn compile
- mvn clean
- mvn test
- mvn package
- mvn install


## Put the resources file in jar file
- This assignment want us to put the resources file in jar file, so we can give the user jar file and not the csv files.
- This progran can be still run successfully.
- Challenge part:
  - 1. We need to first read the 622 folder(csv file) from jar file.
  - 2. Then we need to add plugins in pom.xml to get the resources folder from jar file. 



## Seperate the main class
- We create the main class as access point, and in this file we read the file form jar file and search the word.
- We change the File to and BufferReader that read those file in the file path to use a BufferReader to read the input Stream
`Original`
```java
File f = new File(dir, fileName);
BufferedReader br = new BufferedReader(new FileReader(f));
```
`Changed`
```java
BufferedReader br = new BufferedReader(new InputStreamReader(Demo.class.getClassLoader().getResourceAsStream(fileName.toString())));
```

https://stackoverflow.com/questions/16953897/how-to-read-a-text-file-inside-a-jar

```java
   <build>
        <plugins>
            <plugin>

                <!-- Building an executable jar -->

                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.1.0</version>
                <configuration>
                    <archive>
                        <manifest>

                            <!-- give full qualified name of your main class-->
                            <mainClass>com.pra.Main</mainClass>

                        </manifest>
                    </archive>
                </configuration>
            </plugin>

        </plugins>
        <resources>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>622file/*</include>
                </includes>
            </resource>
        </resources>

    </build>
 ```   
https://stackoverflow.com/questions/574594/how-can-i-create-an-executable-runnable-jar-with-dependencies-using-maven
