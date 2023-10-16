# [Checkstyle](https://github.com/checkstyle/checkstyle)

官方文档：https://checkstyle.sourceforge.io/

Checkstyle 是一个用于检查 Java 源代码是否遵守代码标准或验证规则集（最佳实践）的工具。

默认情况下，它支持 Google Java 样式指南和 Sun 代码约定，但可高度配置。可以使用 ANT 任务和命令行程序来调用它。

可以看到一些开源项目源码都有提供 `checkstyle.xml` 用于协调团队代码质量控制。

使用细节看参考资料，很简单。



## 使用方法

### checkstyle.xml

- [Google's style](https://checkstyle.sourceforge.io/google_style.html)

- [Sun's style](https://checkstyle.sourceforge.io/sun_style.html)

- 开源项目中的checkstyle.xml

- 自定义

  参考官网。

### maven-checkstyle-plugin

```xml
<build>
     <!--公共checkstyle标准配置，可以在子模块中覆盖，修改自定义选项-->
    <pluginManagement>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-checkstyle-plugin</artifactId>
                <version>3.0.0</version>
                <configuration>
                    <configLocation>config/checkstyle/google-checks-6.18.xml</configLocation>
                    <consoleOutput>true</consoleOutput>
                    <encoding>UTF-8</encoding>
                    <consoleOutput>true</consoleOutput>
                    <failsOnError>true</failsOnError>
                    <linkXRef>false</linkXRef>
                    <skip>false</skip>
                    <violationSeverity>error</violationSeverity>
                </configuration>
                <executions>
                    <execution>
                        <!-- 绑定到 Maven install 阶段执行检查, 也可以改成其他阶段 -->
                        <id>install</id>
                        <phase>install</phase>
                        <goals>
                            <goal>checkstyle</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </pluginManagement>

    <!--所有子模块都要执行的plugin-->
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-checkstyle-plugin</artifactId>
        </plugin>
    </plugins>
</build>

<reporting>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-checkstyle-plugin</artifactId>
        </plugin>
    </plugins>
</reporting>
```

### IDEA插件

使用IDEA Checkstyle 插件驱动检查。

+ CheckStyle-IDEA
+ Alibaba Java Coding Guidelines (已停止维护)



## 参考

+ [使用checkstyle来规范你的项目](https://cloud.tencent.com/developer/article/1172528)
