## Gradle
 
 
##  Code
- Code part like the maven project.
- Seperate the main class and function class.
- Change the file and bufferReader read the file to BufferReader read the input stream.


## build.gradle

The different part is we need to add the code in build.grade to includ the file in jar.

```java
jar {
    manifest {
        attributes 'Main-Class': 'com.pra.Main'
    }
    from 'resources', {
        into 'resources'
    }
}
```
https://discuss.gradle.org/t/how-do-i-specify-the-resources-folder-in-a-jar/16054/6
https://stackoverflow.com/questions/9689793/cant-execute-jar-file-no-main-manifest-attribute
## See the file list in jar
```
 jar tf .\build\libs\Gradle_Project-1.0-SNAPSHOT.jar
```
We have successfully included the 622 file in the jar.
![image](https://user-images.githubusercontent.com/79159894/202953373-6b3669b5-d4c5-40ac-a577-a02b884978b3.png)

## Run jar
```
java -jar .\build\libs\Gradle_Project-1.0-SNAPSHOT.jar
```
Jar works successfully.

![image](https://user-images.githubusercontent.com/79159894/202953950-daa61ef3-9b51-4fb2-8ad9-02dbd0de6cba.png)

## command line

- use `up` key we can get the prviouse used command
- use `tab` we can get the file name in the folder. If we want to enter this file, we can add `/` and keep use tab.
