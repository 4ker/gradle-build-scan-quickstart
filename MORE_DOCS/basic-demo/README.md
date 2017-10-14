## Listing All Gradle Tasks

Then run `gradle tasks` (--all, task 和 tasks 一样的)

    Starting a Gradle Daemon (subsequent builds will be faster)

    > Task :tasks

    ------------------------------------------------------------
    All tasks runnable from root project
    ------------------------------------------------------------

    Build Setup tasks
    -----------------
    init - Initializes a new Gradle build.
    wrapper - Generates Gradle wrapper files.

    Help tasks
    ----------
    buildEnvironment - Displays all buildscript dependencies declared in root project 'basic-demo'.
    components - Displays the components produced by root project 'basic-demo'. [incubating]
    dependencies - Displays all dependencies declared in root project 'basic-demo'.
    dependencyInsight - Displays the insight into a specific dependency in root project 'basic-demo'.
    dependentComponents - Displays the dependent components of components in root project 'basic-demo'. [incubating]
    help - Displays a help message.
    model - Displays the configuration model of root project 'basic-demo'. [incubating]
    projects - Displays the sub-projects of root project 'basic-demo'.
    properties - Displays the properties of root project 'basic-demo'.
    tasks - Displays the tasks runnable from root project 'basic-demo'.

    To see all tasks and more detail, run gradle tasks --all

    To see more detail about a task, run gradle help --task <task>


    BUILD SUCCESSFUL in 2s
    1 actionable task: 1 executed

可以看到有两类 task, 一个是 Build Setup tasks, 一个是 Help, 这是两个大类.
每个大类下有具体的指令, 比如 init, wrapper... 可以通过 gradle help --task <task> 来看文档.

## Check Help

`gradle help --task wrapper`:

    > Task :help
    Detailed task information for wrapper

    Path
         :wrapper

    Type
         Wrapper (org.gradle.api.tasks.wrapper.Wrapper)

    Options
         --distribution-type     The type of the Gradle distribution to be used by the wrapper.
                                 Available values are:
                                      ALL
                                      BIN

         --gradle-distribution-url     The URL to download the Gradle distribution from.

         --gradle-version     The version of the Gradle distribution required by the wrapper.

    Description
         Generates Gradle wrapper files.

    Group
         Build Setup


    BUILD SUCCESSFUL in 0s
    1 actionable task: 1 executed

然后运行之:

```
$ gradle wrapper

BUILD SUCCESSFUL in 1s
1 actionable task: 1 executed
```

## Configure a core task and use a plugin

    plugins {
        id 'base'
    }

    // Now add a task that creates a zip archive from the src directory.
    task zip(type: Zip) {
        from 'src'
    }

新建 src/date.txt, 运行, 生成一个压缩包:

    build
    └── distributions
        └── basic-demo.zip 里面有一个文件: date.txt

    1 directory, 1 file

TODO: https://guides.gradle.org/creating-new-gradle-builds/
