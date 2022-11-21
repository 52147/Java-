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
