## Java App

gradle init --type java-application

```
├── build.gradle
├── gradle    
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── gradlew
├── gradlew.bat
├── settings.gradle
└── src
    ├── main
    │   └── java  
    │       └── App.java
    └── test      
        └── java
            └── AppTest.java
```

gradlew 相关: ~/.gradle/wrapper/dists

还自动生成了文档: build/reports/tests/test/index.html

```bash
$ gradle jar  
BUILD SUCCESSFUL in 0s
2 actionable tasks: 2 up-to-date

$ rm build/libs/java-demo.jar 
$ gradle jar                 
BUILD SUCCESSFUL in 0s
2 actionable tasks: 1 executed, 1 up-to-date
```

看这个命令的文档:

```
$ gradle help --task run  

> Task :help
Detailed task information for run

Path
     :run

Type
     JavaExec (org.gradle.api.tasks.JavaExec)

Options
     --debug-jvm     Enable debugging for the process. The process is started suspended and listening on port 5005. [INCUBATING]

Description
     Runs this project as a JVM application

Group
     application


BUILD SUCCESSFUL in 0s
1 actionable task: 1 executed
```

```bash
gradle dependencies
```