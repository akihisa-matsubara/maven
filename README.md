## Maven repository on Github

Github Pagesを利用したMavenリポジトリー  
https://raw.githubusercontent.com/akihisa-matsubara/maven/mvn-repo/  

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
      <password>YOUR-PASSWORD</password>
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
