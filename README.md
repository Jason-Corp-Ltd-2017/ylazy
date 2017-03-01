# YLazy
Web Page Test , 网页性能测试平台



## 核心技术

- phantomjs
- harviewer

## 使用框架

- Springboot,Spring
- scala,Java
- JPA
- Mysql
- jquery
- bootstrap
- adminLTE


## 开源工程源码：

https://github.com/universsky/ylazy


## 关于作者


陈光剑，花名之剑，一剑. 江苏东海人, 号行走江湖一剑客，字之剑。程序员，诗人, 作家。

光剑免费图书馆：https://universsky.github.io/



---

<img src="https://github.com/universsky/ylazy/blob/master/src/main/resources/public/images/ylazy_logo.png">

<img src="https://github.com/universsky/ylazy/blob/master/YLazy.png">

<img src="https://github.com/universsky/ylazy/blob/master/Harviewer.png">



---






## Springboot plus Scala 开发简明教程

### 一 使用maven作为项目构建工具

直接参照pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.light.sword</groupId>
    <artifactId>ylazy</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <scala.version>2.11.8</scala.version>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <encoding>UTF-8</encoding>
        <scala.compat.version>2.11</scala.compat.version>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <java.version>1.8</java.version>
        <platform-bom.version>2.0.3.RELEASE</platform-bom.version>
        <spring-boot-starter-bom.version>1.0.0-SNAPSHOT</spring-boot-starter-bom.version>
        <spring-boot.version>1.3.5.RELEASE</spring-boot.version>
    </properties>


    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.3.5.RELEASE</version>
    </parent>

    <dependencies>
        <!-- scala -->
        <dependency>
            <groupId>org.scala-lang</groupId>
            <artifactId>scala-library</artifactId>
            <version>${scala.version}</version>
        </dependency>

        <dependency>
            <groupId>com.typesafe.scala-logging</groupId>
            <artifactId>scala-logging-slf4j_2.11</artifactId>
            <version>2.1.2</version>
        </dependency>

        <!-- Test -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.specs2</groupId>
            <artifactId>specs2-core_${scala.compat.version}</artifactId>
            <version>2.4.16</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.scalatest</groupId>
            <artifactId>scalatest_${scala.compat.version}</artifactId>
            <version>2.2.4</version>
            <scope>test</scope>
        </dependency>

        <!-- sb -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-velocity</artifactId>
        </dependency>

        <!--test -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
        </dependency>

        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.7</version>
        </dependency>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>
        <dependency>
            <groupId>javax.mail</groupId>
            <artifactId>mail</artifactId>
            <version>1.4.7</version>
        </dependency>
        <dependency>
            <groupId>com.squareup.okhttp3</groupId>
            <artifactId>okhttp</artifactId>
            <version>3.2.0</version>
        </dependency>

        <!--
            devtools可以实现页面热部署（即页面修改后会立即生效，这个可以直接在application.properties文件中配置spring.thymeleaf.cache=false来实现），
             实现类文件热部署（类文件修改后不会立即生效），实现对属性文件的热部署。
             即devtools会监听classpath下的文件变动，并且会立即重启应用（发生在保存时机），注意：因为其采用的虚拟机机制，该项重启是很快的
        -->
        <!--<dependency>-->
        <!--<groupId>org.springframework.boot</groupId>-->
        <!--<artifactId>spring-boot-devtools</artifactId>-->
        <!--<optional>true</optional>&lt;!&ndash; optional=true,依赖不会传递，该项目依赖devtools；之后依赖myboot项目的项目如果想要使用devtools，需要重新引入 &ndash;&gt;-->
        <!--</dependency>-->


    </dependencies>

    <build>
        <sourceDirectory>src/main/scala</sourceDirectory>
        <testSourceDirectory>src/test/scala</testSourceDirectory>
        <plugins>
            <plugin>
                <groupId>org.scala-tools</groupId>
                <artifactId>maven-scala-plugin</artifactId>
                <executions>
                    <execution>
                        <goals>
                            <goal>compile</goal>
                            <goal>testCompile</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <recompileMode>incremental</recompileMode>
                    <scalaVersion>${scala.version}</scalaVersion>
                    <launchers>
                        <launcher>
                            <id>app</id>
                            <mainClass>com.light.sword.ylazy.LightSwordApplication</mainClass>
                            <args>
                                <arg>-deprecation</arg>
                            </args>
                            <jvmArgs>
                                <jvmArg>-Xms256m</jvmArg>
                                <jvmArg>-Xmx2048m</jvmArg>
                            </jvmArgs>
                        </launcher>
                    </launchers>
                </configuration>
                <dependencies>
                    <!-- spring热部署-->
                    <dependency>
                        <groupId>org.springframework</groupId>
                        <artifactId>springloaded</artifactId>
                        <version>1.2.6.RELEASE</version>
                    </dependency>
                </dependencies>
            </plugin>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <!--<configuration>-->
                <!--<fork>true</fork>&lt;!&ndash; 如果没有该项配置，肯呢个devtools不会起作用，即应用不会restart &ndash;&gt;-->
                <!--</configuration>-->
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-dependency-plugin</artifactId>
                <executions>
                    <execution>
                        <phase>package</phase>
                        <goals>
                            <goal>copy-dependencies</goal>
                        </goals>
                    </execution>
                </executions>
                <configuration>
                    <includeScope>system</includeScope>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-eclipse-plugin</artifactId>
                <configuration>
                    <downloadSources>true</downloadSources>
                    <buildcommands>
                        <buildcommand>ch.epfl.lamp.sdt.core.scalabuilder</buildcommand>
                    </buildcommands>
                    <additionalProjectnatures>
                        <projectnature>ch.epfl.lamp.sdt.core.scalanature</projectnature>
                    </additionalProjectnatures>
                    <classpathContainers>
                        <classpathContainer>org.eclipse.jdt.launching.JRE_CONTAINER</classpathContainer>
                        <classpathContainer>ch.epfl.lamp.sdt.launching.SCALA_CONTAINER</classpathContainer>
                    </classpathContainers>
                </configuration>
            </plugin>
        </plugins>
    </build>
    <reporting>
        <plugins>
            <plugin>
                <groupId>org.scala-tools</groupId>
                <artifactId>maven-scala-plugin</artifactId>
                <configuration>
                    <scalaVersion>${scala.version}</scalaVersion>
                </configuration>
            </plugin>
        </plugins>
    </reporting>

    <repositories>
        <repository>
            <id>scala-tools.org</id>
            <name>Scala-Tools Maven2 Repository</name>
            <url>http://scala-tools.org/repo-releases</url>
        </repository>
    </repositories>

    <pluginRepositories>
        <pluginRepository>
            <id>scala-tools.org</id>
            <name>Scala-Tools Maven2 Repository</name>
            <url>http://scala-tools.org/repo-releases</url>
        </pluginRepository>
    </pluginRepositories>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${spring-boot.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>io.spring.platform</groupId>
                <artifactId>platform-bom</artifactId>
                <version>${platform-bom.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>


</project>
```


### 二 Scala plus springboot配置
### 三 SpringBoot plus JPA的持久层框架

####领域类写法

```scala
package com.light.sword.ylazy.entity

import java.util.Date
import javax.persistence.{Entity, GeneratedValue, GenerationType, Id}

import scala.beans.BeanProperty
import scala.language.implicitConversions

@Entity
class LazyTask {
  @Id
  @GeneratedValue(strategy = GenerationType.AUTO)
  @BeanProperty
  var id: Integer = _

  @BeanProperty
  var url: String = _
  @BeanProperty
  var name: String = _

  //用例状态: -1未执行 0失败 1成功
  @BeanProperty
  var state: Integer = _

  @BeanProperty
  var owner: String = _

  @BeanProperty
  var resultJson: String = _

  @BeanProperty
  var executeTimes: Integer = _

  @BeanProperty
  var executor: Integer = _

  @BeanProperty
  var gmtCreate: Date = _

  @BeanProperty
  var gmtModify: Date = _



}
```

####Dao层代码写法

```scala
package com.light.sword.ylazy.dao

import java.util.List

import com.light.sword.ylazy.entity.LazyTask
import org.springframework.data.jpa.repository.Query
import org.springframework.data.repository.CrudRepository

// JavaConversions
import scala.language.implicitConversions

trait LazyTaskDao extends CrudRepository[LazyTask, Integer] {
  def findAll(): List[LazyTask]

  def save(t: LazyTask): LazyTask

  def findOne(id: Integer): LazyTask

  @Query(value = "SELECT * FROM lazy_task where url like '%?1%'", nativeQuery = true)
  def listByUrl(url: String): List[LazyTask]

  @Query(value = "SELECT * FROM lazy_task where name like '%?1%'", nativeQuery = true)
  def listByName(name: String): List[LazyTask]


}

```


### 四 使用Scala调用Spring MVC框架API

####Controller写法实例

```scala
package com.light.sword.ylazy.controller

import java.util.Date

import com.light.sword.ylazy.config.DomainConfig
import com.light.sword.ylazy.dao.LazyTaskDao
import com.light.sword.ylazy.engine.PhantomjsExecutor
import com.light.sword.ylazy.entity.LazyTask
import org.springframework.beans.factory.annotation.Autowired
import org.springframework.ui.Model
import org.springframework.web.bind.annotation._
import org.springframework.web.servlet.ModelAndView

@RestController
class LazyTaskController @Autowired()(val lazyTaskDao: LazyTaskDao,
                                      val phantomjsExecutor: PhantomjsExecutor,
                                      val domainConfig: DomainConfig) {

  @RequestMapping(value = {
    Array("/newTask.do")
  })
  def newTask_do() = {
    new ModelAndView("ylazy/newTask")
  }

  @RequestMapping(value = {
    Array("/ylazy/newTask")
  }, method = Array(RequestMethod.POST))
  @ResponseBody
  def newTask(@ModelAttribute lazyTask: LazyTask) = {
    lazyTask.gmtCreate = new Date
    lazyTask.gmtModify = new Date
    lazyTask.executeTimes = 0
    lazyTask.state = -1
    lazyTaskDao.save(lazyTask)
  }

  @RequestMapping(value = {
    Array("/list.do")
  })
  def list_do(model: Model) = {
    model.addAttribute("lazyTaskList", lazyTaskDao.findAll())
    model.addAttribute("domainName", domainConfig.getDomainName)
    model.addAttribute("port", domainConfig.getPort)

    new ModelAndView("ylazy/list")
  }


  /**
    * 获取一条任务记录
    *
    * @param id
    * @return
    */
  @RequestMapping(value = {
    Array("/lazytask")
  }, method = Array(RequestMethod.GET))
  @ResponseBody
  def findOne(@RequestParam(value = "id") id: Integer) = lazyTaskDao.findOne(id)

  /**
    * 获取一条任务记录的返回json
    *
    * @param id
    * @return
    */
  @RequestMapping(value = {
    Array("/result/{id}")
  }, method = Array(RequestMethod.GET))
  @ResponseBody
  def findResultJson(@PathVariable(value = "id") id: Integer) = lazyTaskDao.findOne(id).resultJson


  /**
    * 执行任务
    * @param id
    * @return
    */
  @RequestMapping(value = {
    Array("/ylazy/runTask")
  }, method = Array(RequestMethod.GET))
  @ResponseBody
  def runTask(@RequestParam(value = "id") id: Integer) = {
    phantomjsExecutor.ylazyById(id)
  }


  @RequestMapping(value = {
    Array("/ylazy")
  }, method = Array(RequestMethod.GET))
  @ResponseBody
  def ylazy(@RequestParam(value = "url") url: String) = phantomjsExecutor.ylazy(url)


}

```
 


### 五 Scala with Java混合编程
由于Scala代码最终也是编译成为JVM上的ByteCode，所以与所有运行在JVM上的语言无缝集成。


参看LazyTaskController.scala对PhantomjsExecutor.java类的调用。



































