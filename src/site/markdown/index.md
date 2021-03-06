Introduction
============

This plugin is generally meant to be used with another plugin that requires
the phantomjs binary. The plugin will download the binary and make it
executable. Then it will set the property, `phantomjs.binary`, to the path
to the binary.

This example shows a typical usage with the [jasmine-maven-plugin](http://searls.github.io/jasmine-maven-plugin/).

```
<project>
  ...
  <build>
    <plugins>
      <plugin>
        <groupId>com.github.klieber</groupId>
        <artifactId>phantomjs-maven-plugin</artifactId>
        <version>${phantomjs-maven-plugin.version}</version>
        <executions>
          <execution>
            <goals>
              <goal>install</goal>
            </goals>
          </execution>
        </executions>
        <configuration>
          <version>1.9.2</version>
        </configuration>
      </plugin>
      <plugin>
        <groupId>com.github.searls</groupId>
        <artifactId>jasmine-maven-plugin</artifactId>
        <version>${jasmine-maven-plugin.version}</version>
        <executions>
          <execution>
            <goals>
              <goal>test</goal>
            </goals>
          </execution>
        </executions>
        <configuration>
          <webDriverClassName>org.openqa.selenium.phantomjs.PhantomJSDriver</webDriverClassName>
          <webDriverCapabilities>
            <phantomjs.binary.path>${phantomjs.binary}</phantomjs.binary.path>
          </webDriverCapabilities>
        </configuration>
      </plugin>
      ...
    </plugins>
  </build>
  ...
</project>
```
