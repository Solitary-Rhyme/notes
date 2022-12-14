# 04 - xml

[toc]

### 1. xml基础

- xml是可扩展的标记性语言

  xml的主要作用：

  1. 用来保存数据，这些数据具有自我描述性 
  2. 作为项目或模块的配置文件
  3. 作为网络传输数据的格式（现以json为主）

- 一个简单的xml文件示例

  ```xml
  <?xml version="1.0" encoding="utf-8" ?>
  <!--xml文件的声明-->
  <books>
      <!--元素和元素属性-->
      <book sn="12354684">
          <name>AAA</name>
          <author>BBB</author>
      </book>
      <book sn="4684654">
          <name>AAA</name>
          <author>BBB</author>
      </book>
  </books>
  ```

  

### 2. xml元素

- xml元素指的是从开始标签直到结束标签的部分。元素可包含其它元素，文本或两者的混合。元素也可以拥有属性
- **命名规则**
  1. 名称可以包含字母，数字以及其它的字符
  2. 名称不能以数字或标点符号开始
  3. 名称不建议以字符"xml"(XML,Xml等)开始
  4. 名称不能包含空格
- xml中的元素也分成单标签和双标签：
  - 单标签：`<标签名 属性="值" 属性="值" .../>`
  - 双标签：`<标签名 属性="值" 属性="值" ...>文本数据或子标签</标签名>`

- **xml属性**

  xml的标签属性和html的标签属性非常类似，属性可以提供元素的额外信息。

  一个标签上可以书写多个属性。每个属性的值必须使用引号引起来，属性的书写规则和标签的书写规则一致



### 3.xml语法规则

1. 所有xml元素都必须有关闭标签(必须闭合)

2. xml标签对大小写敏感

3. xml必须正确地嵌套

4. xml文档必须有根元素

   根元素就是没有父标签的元素，根元素必须唯一

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <!--xml文件的声明-->
   <books>
       <!--元素和元素属性-->
       <book sn="12354684">
       </book>
       <book sn="4684654">
       </book>
   </books>
   <bookss></bookss>
   
   <!--
   此处book标签具有父元素,所以无法称为根元素
   books标签具有并列的bookss标签，两者都无法称之为根元素
   把bookss标签删除后,books唯一且无父元素，可以称之为根元素
   -->
   ```

5. xml的属性值必须加引号

6. 文本区域(CDATA区)

   如果需要大量的输入特殊字符(如<>等)，可以将文本放在文本区域中

   ```xml
   <![CDATA][把输入的字符原样显示，不会解析]>
   ```

   

### 4. xml解析

- 作为标记语言,html文件和xml文件可以使用制定的dom技术来解析。DOM将xml文档作为一个树形结构，而树叶被定义为节点。现在主流的解析技术是Dom4j，下面介绍这一技术