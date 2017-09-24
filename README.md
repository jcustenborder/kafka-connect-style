# Introduction

This project contains common resources to help consolidate configuration for kafka connect projects.

```xml
<properties>
    <kafka-connect-style.version>[1.0.0.0,1.0.0.1000)</kafka-connect-style.version>
</properties>
```

## Assemblies

```xml
<plugin>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>2.6</version>
    <executions>
        <execution>
            <id>assembly-single-package</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
            <configuration>
                <appendAssemblyId>false</appendAssemblyId>
                <descriptorRefs>
                    <descriptorRef>package</descriptorRef>
                </descriptorRefs>
                <formats>
                    <format>tar.gz</format>
                </formats>
                <tarLongFileMode>posix</tarLongFileMode>
            </configuration>
        </execution>
        <execution>
            <id>assembly-single-dir</id>
            <phase>package</phase>
            <goals>
                <goal>single</goal>
            </goals>
            <configuration>
                <attach>false</attach>
                <finalName>kafka-connect-target</finalName>
                <appendAssemblyId>false</appendAssemblyId>
                <descriptorRefs>
                    <descriptorRef>package</descriptorRef>
                </descriptorRefs>
                <formats>
                    <format>dir</format>
                </formats>
            </configuration>
        </execution>
    </executions>
    <dependencies>
        <dependency>
            <groupId>com.github.jcustenborder.kafka.connect</groupId>
            <artifactId>kafka-connect-style-assemblies</artifactId>
            <version>${kafka-connect-style.version}</version>
        </dependency>
    </dependencies>
</plugin>
```

## Checkstyle

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>2.17</version>
    <executions>
        <execution>
            <id>validate</id>
            <phase>validate</phase>
            <configuration>
                <configLocation>checkstyle.xml</configLocation>
                <encoding>UTF-8</encoding>
                <consoleOutput>true</consoleOutput>
                <failsOnError>true</failsOnError>
                <includeResources>false</includeResources>
                <includeTestResources>false</includeTestResources>
                <sourceDirectory>${project.build.sourceDirectory}</sourceDirectory>
            </configuration>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
    <dependencies>
        <dependency>
            <groupId>com.github.jcustenborder.kafka.connect</groupId>
            <artifactId>kafka-connect-style-checkstyle</artifactId>
            <version>${kafka-connect-style.version}</version>
        </dependency>
    </dependencies>
</plugin>
```

## Licensing

```xml
<plugin>
    <groupId>com.mycila</groupId>
    <artifactId>license-maven-plugin</artifactId>
    <version>3.0</version>
    <configuration>
        <header>APACHE-2.txt</header>
        <properties>
            <owner>Jeremy Custenborder</owner>
            <email>jcustenborder@gmail.com</email>
        </properties>
        <excludes>
            <exclude>**/README</exclude>
            <exclude>src/test/resources/**</exclude>
            <exclude>src/main/resources/**</exclude>
            <exclude>src/assembly/**</exclude>
        </excludes>
    </configuration>
    <dependencies>
        <dependency>
            <groupId>com.github.jcustenborder.kafka.connect</groupId>
            <artifactId>kafka-connect-style-licensing</artifactId>
            <version>${kafka-connect-style.version}</version>
        </dependency>
    </dependencies>
</plugin>
```