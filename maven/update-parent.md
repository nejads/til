# How to update parent automatically 

Let's imagine you have defined a parent in your project. something like: 
```        
    <parent>
        <groupId>se.soroush</groupId>
        <artifactId>my-master-pom</artifactId>
        <version>1</version>
    </parent>
```               
when you update the master pom the child projects do not get the updated parent version. It is possible to update the parent project by using a plugin called `versions-maven-plugin`. You need to set an execution goal for it. In this example, I put the load to `install`. It is also in the parent pom so all the children will get this plugin when they update to the version that includes it. The first update must be done manually though. After that, the plugin reads the most updated parent version from the m2 remote folder and updates the parent version upon a `mvn install`. 
```
    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.codehaus.mojo</groupId>
                    <artifactId>versions-maven-plugin</artifactId>
                    <version>2.8.1</version>
                    <executions>
                        <execution>
                            <phase>install</phase>
                            <goals>
                                <goal>update-parent</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
            </plugins>
        </pluginManagement>
        <plugins>
          <plugin>
              <groupId>org.codehaus.mojo</groupId>
              <artifactId>versions-maven-plugin</artifactId>
          </plugin>
        </plugins>
    </build>
``` 
