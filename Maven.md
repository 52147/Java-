# Maven

## Traditional project
- jar pckages do not have the same version.
- Hard to maintain. For example, open Project that develop at linux environment at window environmenmt will appear some error.

## What is Maven
- Project management: 
  - Maven is a tool for managing the project based on the concept of project object model(POM).
  - One project is like a object.
- Pom.xml: contains the information of one project.
- Dependency management: Mange the project by Maven. Our project can be a resource for other use, and we can also use resource from others projects. 
- Build Lifecycle : 
  - process of POM -> Dependency
  - use many plugin to build the different goal. goal: jar package, source code, war, xml 
pom.xml -> POM -> Dependency -> local repository -> remote repository -> Internet -> central repository

https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
