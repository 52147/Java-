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
