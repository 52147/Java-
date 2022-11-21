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
## See the file list in jar
```
 jar tf .\build\libs\Gradle_Project-1.0-SNAPSHOT.jar
```
We have successfully included the 622 file in the jar.
![image](https://user-images.githubusercontent.com/79159894/202953373-6b3669b5-d4c5-40ac-a577-a02b884978b3.png)
