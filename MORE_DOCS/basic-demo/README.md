## Listing All Gradle Tasks

Then run `gradle tasks` (--all, task 和 tasks 一样的)

```
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
```

可以看到有两类 task, 一个是 Build Setup tasks, 一个是 Help, 这是两个大类.
每个大类下有具体的指令, 比如 init, wrapper... 可以通过 gradle help --task <task> 来看文档.

## Check Help

`gradle help --task wrapper`:

```
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
```

然后运行之:

```
$ gradle wrapper

BUILD SUCCESSFUL in 1s
1 actionable task: 1 executed
```

wrapper 命令生成和当前 gradle 一样版本的命令行打包. 运行后多出来一些文件:

```
$ git status
Untracked files:
  (use "git add <file>..." to include in what will be committed)

        gradle/
        gradlew
        gradlew.bat
        
$ tree gradle
gradle
└── wrapper
    ├── gradle-wrapper.jar
    └── gradle-wrapper.properties

1 directory, 2 files

$ cat gradle/wrapper/gradle-wrapper.properties 
distributionBase=GRADLE_USER_HOME
distributionPath=wrapper/dists
zipStoreBase=GRADLE_USER_HOME
zipStorePath=wrapper/dists
distributionUrl=https\://services.gradle.org/distributions/gradle-4.2-bin.zip
```

终于知道这个 w 是啥意思了...

## Gradle Properties

`./gradlew properties`:

```
> Task :properties

------------------------------------------------------------
Root project
------------------------------------------------------------

allprojects: [root project 'gradle-build-scan-quickstart']
ant: org.gradle.api.internal.project.DefaultAntBuilder@5d9d30a1
antBuilderFactory: org.gradle.api.internal.project.DefaultAntBuilderFactory@35f94b05
archivesBaseName: gradle-build-scan-quickstart
artifacts: org.gradle.api.internal.artifacts.dsl.DefaultArtifactHandler_Decorated@7f914e99
asDynamicObject: DynamicObject for root project 'gradle-build-scan-quickstart'
assemble: task ':assemble'
baseClassLoaderScope: org.gradle.api.internal.initialization.DefaultClassLoaderScope@28ec8327
buildDependents: task ':buildDependents'
buildDir: /Users/zxtang/git/gradle-build-scan-quickstart/build
buildFile: /Users/zxtang/git/gradle-build-scan-quickstart/build.gradle
buildNeeded: task ':buildNeeded'
buildScan: com.gradle.scan.plugin.internal.api.e@1c40b6a3
buildScanPublishPrevious: task ':buildScanPublishPrevious'
buildScriptSource: org.gradle.groovy.scripts.TextResourceScriptSource@639e774d
buildscript: org.gradle.api.internal.initialization.DefaultScriptHandler@160e1821
check: task ':check'
childProjects: {}
class: class org.gradle.api.internal.project.DefaultProject_Decorated
classLoaderScope: org.gradle.api.internal.initialization.DefaultClassLoaderScope@5a37547c
classes: task ':classes'
compileJava: task ':compileJava'
compileTestJava: task ':compileTestJava'
components: SoftwareComponentInternal set
configurationActions: org.gradle.configuration.project.DefaultProjectConfigurationActionContainer@43db1437
configurationTargetIdentifier: org.gradle.configuration.ConfigurationTargetIdentifier$1@536f371e
configurations: configuration container
convention: org.gradle.api.internal.plugins.DefaultConvention@35c6e242
defaultArtifacts: org.gradle.api.internal.plugins.DefaultArtifactPublicationSet_Decorated@5532c432
defaultTasks: []
deferredProjectConfiguration: org.gradle.api.internal.project.DeferredProjectConfiguration@4e53180f
dependencies: org.gradle.api.internal.artifacts.dsl.dependencies.DefaultDependencyHandler_Decorated@64ae011c
depth: 0
description: null
displayName: root project 'gradle-build-scan-quickstart'
distsDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/distributions
distsDirName: distributions
docsDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/docs
docsDirName: docs
ext: org.gradle.api.internal.plugins.DefaultExtraPropertiesExtension@66782b39
extensions: org.gradle.api.internal.plugins.DefaultConvention@35c6e242
fileOperations: org.gradle.api.internal.file.DefaultFileOperations@25a86090
fileResolver: org.gradle.api.internal.file.BaseDirFileResolver@73ed874a
gradle: build 'gradle-build-scan-quickstart'
group: 
identityPath: :
inheritedScope: org.gradle.api.internal.ExtensibleDynamicObject$InheritedDynamicObject@675fceca
jar: task ':jar'
javadoc: task ':javadoc'
layout: org.gradle.api.internal.file.DefaultProjectLayout@40d900fb
libsDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/libs
libsDirName: libs
logger: org.gradle.internal.logging.slf4j.OutputEventListenerBackedLogger@26935490
logging: org.gradle.internal.logging.services.DefaultLoggingManager@395b50df
modelRegistry: org.gradle.model.internal.registry.DefaultModelRegistry@20ebe0a0
modelSchemaStore: org.gradle.model.internal.manage.schema.extract.DefaultModelSchemaStore@283df29e
module: org.gradle.api.internal.artifacts.ProjectBackedModule@e57f562
name: gradle-build-scan-quickstart
normalization: org.gradle.normalization.internal.DefaultInputNormalizationHandler_Decorated@14b604dd
objects: org.gradle.api.internal.model.DefaultObjectFactory@7788733c
parent: null
parentIdentifier: null
path: :
pluginManager: org.gradle.api.internal.plugins.DefaultPluginManager_Decorated@899638d
plugins: [org.gradle.api.plugins.HelpTasksPlugin@49918643, com.gradle.scan.plugin.BuildScanPlugin@5e91aeae, org.gradle.language.base.plugins.LifecycleBasePlugin@5d83abc1, org.gradle.api.plugins.BasePlugin@1dbe6040, org.gradle.api.plugins.ReportingBasePlugin@795d771, org.gradle.platform.base.plugins.ComponentBasePlugin@702eef7a, org.gradle.language.base.plugins.LanguageBasePlugin@59298051, org.gradle.platform.base.plugins.BinaryBasePlugin@52b1c774, org.gradle.api.plugins.JavaBasePlugin@6a755b55, org.gradle.api.plugins.JavaPlugin@60e70d74]
processOperations: org.gradle.api.internal.file.DefaultFileOperations@25a86090
processResources: task ':processResources'
processTestResources: task ':processTestResources'
project: root project 'gradle-build-scan-quickstart'
projectConfigurator: org.gradle.api.internal.project.BuildOperationCrossProjectConfigurator@4f77c902
projectDir: /Users/zxtang/git/gradle-build-scan-quickstart
projectEvaluationBroadcaster: ProjectEvaluationListener broadcast
projectEvaluator: org.gradle.configuration.project.LifecycleProjectEvaluator@6b43bcdd
projectPath: :
projectRegistry: org.gradle.api.internal.project.DefaultProjectRegistry@5fe6231a
properties: {...}
providers: org.gradle.api.internal.provider.DefaultProviderFactory@1ca0a660
reporting: org.gradle.api.reporting.ReportingExtension_Decorated@6d6e532f
reportsDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/reports
repositories: repository container
resourceLoader: org.gradle.internal.resource.transfer.DefaultUriTextResourceLoader@1b3daf0b
resources: org.gradle.api.internal.resources.DefaultResourceHandler@75adb185
rootDir: /Users/zxtang/git/gradle-build-scan-quickstart
rootProject: root project 'gradle-build-scan-quickstart'
scriptHandlerFactory: org.gradle.api.internal.initialization.DefaultScriptHandlerFactory@6ca79af6
scriptPluginFactory: org.gradle.configuration.ScriptPluginFactorySelector@734f4b66
serviceRegistryFactory: org.gradle.internal.service.scopes.ProjectScopeServices$4@57cf7f3
services: ProjectScopeServices
sourceCompatibility: 1.8
sourceSets: SourceSet container
standardOutputCapture: org.gradle.internal.logging.services.DefaultLoggingManager@395b50df
state: project state 'EXECUTED'
status: integration
subprojects: []
targetCompatibility: 1.8
tasks: task set
test: task ':test'
testClasses: task ':testClasses'
testReportDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/reports/tests
testReportDirName: tests
testResultsDir: /Users/zxtang/git/gradle-build-scan-quickstart/build/test-results
testResultsDirName: test-results
version: unspecified


BUILD SUCCESSFUL in 5s
1 actionable task: 1 executed

Publishing build scan...
https://gradle.com/s/dkqupa35hrex6
```

可以修改 property, 在 build.gradle 里面添加:

```
description = 'A trivial Gradle build'
version = '1.0'
```

然后再次运行, 并 grep 'A trivial Gradle build':

```
$ gradle properties | grep 'A trivial Gradle build'
Root project - A trivial Gradle build
description: A trivial Gradle build
```

property 必须有这个变量才能设置.

## Configure a core task and use a plugin

添加一个任务:

```groovy
// Define a task called copy of type Copy (note the capital letter) that 
// copies the src directory to a new directory called dest. 
// (You don’t have to create the dest directory — the task will do it for you.)
task copy(type: Copy) {
    from 'src'
    into 'dest'
}
```

运行之. 复制成功.

运行 gradle clean 可以清空 build 文件夹.

## the Gradle Plugin Portal / 插件中心

https://plugins.gradle.org/

The assemble and build tasks aren’t useful in this project, 
because they are associated with compilation and generation of a release artifact. 
Many of the language plugins, like the java plugin, are created on top the base plugin.

```
plugins {
    id 'base'
}

// Now add a task that creates a zip archive from the src directory.
task zip(type: Zip) {
    from 'src'
}
```

新建 src/date.txt, 运行, 生成一个压缩包:

```
build
└── distributions
    └── basic-demo.zip 里面有一个文件: date.txt

1 directory, 1 file
```

## Add a "Hello, World!" task

```groovy
task hello {
    // Create an ad-hoc (临时, 专门) task and add an action using doLast
    doLast {
        println 'Hello, World!'
    }
}
```

仔细看一下文档: https://guides.gradle.org/writing-gradle-tasks/ (DONE)

加上 group 和 description, 前者在 task listing 的时候用到, 后者就是一个文档罗.

```
task hello {
    group 'Welcome'
    description 'Produces a greeting'

    doLast {
        println 'Hello, World'
    }
}
```

`$ gradle tasks`:

```
Welcome tasks
-------------
hello - Produces a greeting

$ gradle help --task hello  

> Task :help
Detailed task information for hello

Path
     :hello

Type
     Task (org.gradle.api.Task)

Description
     Produces a greeting

Group
     Welcome


BUILD SUCCESSFUL in 0s
1 actionable task: 1 executed
```

来一点定制:

```groovy
// As the build DSL in a build.gradle file is a Groovy-base DSL, the class will be a Groovy class.
class Greeting extends DefaultTask {   
    String message 
    String recipient

    // Annotate the default task action.
    @TaskAction 
    void sayGreeting() {
        // Print the message using a standard Groovy interpolated string.
        println "${message}, ${recipient}!" 
        println "${getDescription()}"
    }
}

task hello (type : Greeting) { 
    group 'Welcome'
    description 'Produces a world greeting'
    message 'Hello' 
    recipient 'World'
}
```

```bash
$ gradle hello

> Task :hello
Hello, World!
Produces a world greeting


BUILD SUCCESSFUL in 0s
1 actionable task: 1 executed
```

## Learn Groovy in Y Minutes

文档: https://github.com/adambard/learnxinyminutes-docs/blob/master/groovy.html.markdown

### 环境设置 / REPL

```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh" 
sdk version
```

这玩意没装上... 这了一下 REPL, 发现 IDEA 自己的 groovy console 就很好,
在 Tools -- Groovy Console,

Command+Enter 运行.

### 简单语法

```groovy
def x = 5
y = false                               // 也可以不要 def
println x.toString() + y.toString()

// interpolation
println "${x} ${y}"                     // 单引号可以 interpolate, 双引号不行

// list litaral
list = [2, false, "good"]
println list

// list add/remove
list << [true, false]                   // list.add
list = list - false                     // list.remove

// 实际测了一下, 发现 - 和 remove 不太一样, 前者可以跟一个 [a,b], 然后把原来 list 里的 a 和 b 都 remove,
// 后者如果传入 [a,b] 则会把 [a,b] remove 掉

println "iteration"
list.each { println "item: $it"}
println "iteration with index"
list.eachWithIndex { it, i -> println "$i: $it" }

item = "good"
println item in list
println list.contains(item)             // containsAll

list.sort()                             // inplace
list.sort(false)                        // sort in a copy
list.clear()

// map
def map1 = [:]
def map2 = ['k':'v', 'k2': 'v2']
map1.put('key', 'value')
map2.each { println "$it.key: $it.value" }
// containsKey, containsValue
// keySet(), values(), entrySet() (这些和 Java 的 map 没啥区别)

// 字符串的比较
if ("go"+"od"=="good") {
    println "可以直接用 == 符号"
}

// ternary operator 
x = condition ? a : b
// The Elvis Operator
y = obj.field ?: 'default'
// 和 JS 那个很有区别, field 不能使 undefined, 有这个 field, 为空才能走到后面的 default

// range 左右都是闭合的
(0..20) // 0, 1, ..., 20
(0..20).toArray()
```

### Groovy Beans

- 如果有 access modifier, 就生成一个 field
- 如果没有, 就是 private, 并自动生成 getter 和 setter
- 如果是 final, 就没有 getter / setter
- 也可以自定义 getter 和 setter (这个 groovy 也没法拦着把...)
- 

```groovy
class Foo {
    // read only property
    final String name = "Roberto"

    // read only property with public getter and protected setter
    String language
    protected void setLanguage(String language) { this.language = language }

    // dynamically typed property
    def lastName
}
```

### Operator Overloading

```groovy
// spread operator
["good", "bad"]*.toUpperCase()
["good", "bad"].collect { it?.toUpperCase() }

// safe navigation operator
println null?.toString()
```

### Closures

```groovy
clos = { println "Hello World!" }
clos()

clos = { a, b -> println "$a $b" }
clos("hello", "world")

// 如果只有一个变量, 可以用 it, 而不用声明
```

### Memoize

memoize 一个 closure, 很方便地 cache:

```groovy
def cl = {a, b ->
    sleep(3000) // simulate some time consuming processing
    a + b
}

mem = cl.memoize()

def callClosure(a, b) {
    def start = System.currentTimeMillis()
    mem(a, b)
    println "Inputs(a = $a, b = $b) - took ${System.currentTimeMillis() - start} msecs."
}

callClosure(1, 2)
callClosure(1, 2)
callClosure(2, 3)
callClosure(2, 3)
callClosure(3, 4)
callClosure(3, 4)
callClosure(1, 2)
callClosure(2, 3)
```

### Expando

这个可以很灵活地定义逻辑 (很像脚本语言了)

```groovy
def user = new Expando(name:"Roberto")
assert 'Roberto' == user.name

user.lastName = 'Pérez'
assert 'Pérez' == user.lastName

user.showInfo = { out ->
    out << "Name: $name"
    out << ", Last name: $lastName"
}

def sw = new StringWriter()
println user.showInfo(sw)
```

### Metaprogramming (MOP)

添加函数, 类似于 JS 给 prototype 加方法:

```groovy
String.metaClass.testAdd = { /* closure */ }
```

intercepting 方法, 看上去可以用来实现 AOP:

```groovy
//Intercepting method calls
class Test implements GroovyInterceptable {
    def sum(Integer x, Integer y) { x + y }

    def invokeMethod(String name, args) {
        System.out.println "Invoke method $name with args: $args"
    }
}

def test = new Test()
test?.sum(2,3)
test?.multiply(2,3)
```

propertyMissing 功能, 目测这个是利用 Java 的反射功能来 getField 实现的:

```groovy
class Foo {
   def propertyMissing(String name) { name }
}
def f = new Foo()

assertEquals "boo", f.boo
```

### TypeChecked and CompileStatic (TODO)

Groovy, by nature, is and will always be a dynamic language but 
it supports typechecked and compilestatic.
