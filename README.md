# MyBatisGenerator Maven 插件 

## 1.设置`mysql-connector-java` Jar 包路径

```xml
<classPathEntry  location="K:\maven\maven3.5\repository\mysql\mysql-connector-java\5.1.44\mysql-connector-java-5.1.44.jar"/>
```

## 2. 设置数据库连接信息

```xml
<jdbcConnection driverClass="com.mysql.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/mybatisgeneratordemo"
                        userId="root"
                        password="root">
</jdbcConnection>
```



## 3.设置 `实体`,`mapper`,`.xml`生成路径

```xml
<!--生成实体类 指定包名 以及生成的地址 （可以自定义地址，但是路径不存在不会自动创建  使用Maven生成在target目录下，会自动创建） -->
        <javaModelGenerator targetPackage="com.xing.model" targetProject="src\main\java">
            <property name="enableSubPackages" value="false" />
            <property name="trimStrings" value="false" />
        </javaModelGenerator>
        <!--生成SQLMAP文件 -->
        <sqlMapGenerator targetPackage="mapper"  targetProject="src\main\resources">
            <property name="enableSubPackages" value="false" />
        </sqlMapGenerator>

        <!--生成Dao文件 可以配置 type="XMLMAPPER"生成xml的dao实现  context id="DB2Tables" 修改targetRuntime="MyBatis3"  -->
        <javaClientGenerator type="XMLMAPPER" targetPackage="com.xing.mapper" targetProject="src\main\java">
            <property name="enableSubPackages" value="false" />
        </javaClientGenerator>
```



## 4.指定 `table`

```xml
<!--对应数据库表 mysql可以加入主键自增 字段命名 忽略某字段等-->
<table tableName="role" domainObjectName="Role"
               enableCountByExample="false"
               enableInsert="true"
               enableUpdateByExample="false"
               enableUpdateByPrimaryKey="true"
               enableDeleteByExample="false"
               enableDeleteByPrimaryKey="true"
               enableSelectByPrimaryKey="true"
               selectByPrimaryKeyQueryId="true"
               enableSelectByExample="false"
               selectByExampleQueryId="true">
            <property name="useActualColumnNames" value="true"/>
</table>
```

