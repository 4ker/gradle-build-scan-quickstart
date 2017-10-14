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

## Configure a core task and use a plugin

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

TODO: https://guides.gradle.org/creating-new-gradle-builds/

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
