## Maven repository on Github

Github Pagesを利用したMavenリポジトリー  
https://raw.githubusercontent.com/akihisa-matsubara/maven/mvn-repo/  

### 利用法
ファイル `~/.m2/settings.xml` に、次の例のように  
`<repository>` の情報を追加します。  
```xml
  <activeProfiles>
    <activeProfile>github</activeProfile>
  </activeProfiles>

  <profiles>
    <profile>
      <id>github</id>
      <repositories>
        <repository>
          <id>central</id>
          <url>https://repo.maven.apache.org/maven2</url>
          <releases><enabled>true</enabled></releases>
          <snapshots><enabled>true</enabled></snapshots>
        </repository>
        <repository>
          <id>github</id>
          <name>Sample Maven Repository</name>
          <url>https://raw.githubusercontent.com/akihisa-matsubara/maven/mvn-repo</url>
        </repository>
      </repositories>
    </profile>
  </profiles>
```

## リリース用設定
### GitHubアカウントの設定
次に GitHub のアカウント情報を設定します。  
ファイル `~/.m2/settings.xml` に、次の例のように  
`<server>` の情報を追加します。  

```xml
  <settings>
    <servers>
      <server>
        <id>github</id>
        <username>YOUR-USERNAME</username>
        <password>TOKEN</password>
      </server>
    </servers>
  </settings>
```

### pom.xml への設定
```xml
    <properties>
        <!-- maven repository settings -->
        <github.global.server>github</github.global.server>
        <git.repositoryOwner>akihisa-matsubara</git.repositoryOwner>
        <git.repositoryName>maven</git.repositoryName>
        <git.branchName>mvn-repo</git.branchName>
    </properties>

    <repositories>
        <repository>
            <id>github-maven</id>
            <url>https://raw.githubusercontent.com/${git.repositoryOwner}/${git.repositoryName}/${git.branchName}/</url>
            <snapshots>
                <enabled>true</enabled>
                <updatePolicy>always</updatePolicy>
            </snapshots>
        </repository>
    </repositories>
```
