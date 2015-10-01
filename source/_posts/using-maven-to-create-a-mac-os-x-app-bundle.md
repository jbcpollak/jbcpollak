title: Using Maven to create a Mac OS X app bundle
tags:
  - java
  - mac
  - maven
  - OS X
id: 53
categories:
  - Tech
date: 2007-11-05 15:57:24
---

I came across [this post](http://simplericity.com/2007/09/19/1190234671861.html) and [this Maven plugin](http://mojo.codehaus.org/osxappbundle-maven-plugin/) today. Call me cynical, but I was shocked when it worked out of the box, building our application as a Mac friendly .app which can be run with a double click.

To test it out, all I did was change into our application's trunk directory and ran:

`mvn package osxappbundle:bundle -DmainClass=com.mypkg.MyMain`

And it worked!

So I extended integrated it into our pom.xml with the following. Now whenever our app is packaged on a Mac, in addition to the other artifacts, an .app, .dmg, and .zip of the My App tool will be created.

<pre>
<profiles>
   ....
        <profile>
            <id>package-osx-bundle</id>
            <activation>
                <os>
                    <family>mac</family>
                </os>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>osxappbundle-maven-plugin</artifactId>
                        <configuration>
                            <mainClass>com.mypkg.MyMain</mainClass>
                            <bundleName>My App</bundleName>
                            <jvmVersion>1.5+</jvmVersion>
                        </configuration>
                        <executions>
                            <execution>
                                <phase>package</phase>
                                <!-- append to the packaging phase. -->
                                <goals>
                                    <goal>bundle</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
    </profiles>
</pre>
