# First Spring Boot App

## 创建项目
基于[Spring Initializr](http://start.spring.io/)创建基础项目。根据需要选择依赖组件。  

## 主页视图
为`/`根路径返回`readingList`视图名。

## Spring Data JPA
- 模型对象添加`@Entity`注解。  
- 扩展`JpaRepository`接口定义新的持久化方法。

## POST API创建Book
- 访问[home page](http://localhost:8000)填写表单数据后点击`Submit`提交，后台映射方法`ReadingListController.addToReadingList()`将表单数据转换为`Book`对象后调用JPA接口存入DB。  
- 然后返回重定向`"redirect:/{reader}"`显示已添加的Book列表。

