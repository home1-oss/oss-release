-----
如果你正在通过git服务查看此文档，请移步项目网站或gitbook查看文档，因为git服务生成的文档链接有问题。
+ [gitbook](http://mvnsite.internal/oss-develop/gitbook)
+ [RELEASE版网站](http://mvnsite.internal/oss/staging)
+ [SNAPSHOT版网站](http://mvnsite.internal/oss-develop/staging)
-----

# oss-release依赖管理平台

oss-release整合了[oss-common-dependencies](https://github.com/home1-oss/oss-release/tree/develop)和[oss-lib](https://github.com/home1-oss/oss-lib).
> [oss-common-dependencies](https://github.com/home1-oss/oss-common-dependencies/tree/develop)定义技术栈的外部软件依赖.
> [oss-lib](https://github.com/home1-oss/oss-lib)提供易于使用的库, 直接使用oss-common-dependencies进行依赖管理.
> 除oss-lib项目直接使用oss-common-dependencies外, 其它项目应该通过oss-release间接地使用oss-common-dependencies并引入oss-lib.

取决于你使用的spring-boot版本, oss-lib无法针对所有spring-boot版本提供全部软件包, 如需使用全部功能, 需使用最新的spring-boot版本. 

## 使用方法

你的项目可以使用oss-release作为parent, 这样间接地以oss-build为ancestor.

    <parent>
        <groupId>cn.home1</groupId>
        <artifactId>oss-release-spring-boot-${spring-boot.version}</artifactId>
        <version>${oss-release.version}</version>
    </parent>

或者在dependencyManagement中import它.

    <!-- 以oss-build为parent是可选的 -->
    <parent>
        <groupId>cn.home1</groupId>
        <artifactId>oss-build</artifactId>
        <version>${oss-build.version}</version>
    </parent>
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>cn.home1</groupId>
                <artifactId>oss-release-spring-boot-${spring-boot.version}</artifactId>
                <version>${oss-release.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
