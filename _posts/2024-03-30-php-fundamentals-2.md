---
layout: post
title: "PHP基本语法2"
date: 2024-03-30 15:00:34 -0700
categories: php
---

# 先导知识：Git

参考《Git以及tortoiseGit的使用指南》。

> 文档作者**19级计算机应用工程孙卓凡**，感谢他为课程文档的建设做出的贡献🎉。
> 

# 项目实战：课程评价APP

在本次的实验中我们来构建一个基于PHP的课程评价APP，此网站的静态网页代码如下，该项目使用了Bootstrap框架：

1. **`index.html`**:

```html
<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/5.3.1/css/bootstrap.min.css" rel="stylesheet">
  <title>课程评价</title>
</head>
<body>
  <nav class="navbar navbar-expand-sm navbar-light bg-light mb-4">
    <div class="container">
      <a class="navbar-brand" href="#">课程评价中心</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="切换导航">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
         <li class="nav-item">
              <a class="nav-link" href="./index.html">首页</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="./reviews.html">评价</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="./about.html">关于我们</a>
            </li>
        </ul>
      </div>
  </div>
</nav>

<main>
  <div class="container d-flex flex-column align-items-center">
    <img src="/course-review-app/img/logo.png" class="w-25 mb-3" alt="">
    <h2>课程评价</h2>
    <p class="lead text-center">为你所上的课程留下评价</p>
    <form action="" class="mt-4 w-75">
      <div class="mb-3">
        <label for="name" class="form-label">你的姓名</label>
        <input type="text" class="form-control" id="name" name="name" placeholder="请输入你的姓名">
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">你的邮箱</label>
        <input type="email" class="form-control" id="email" name="email" placeholder="请输入你的邮箱">
      </div>
      <div class="mb-3">
        <label for="course" class="form-label">课程名称</label>
        <input type="text" class="form-control" id="course" name="course" placeholder="请输入课程名称">
      </div>
      <div class="mb-3">
        <label for="body" class="form-label">评价内容</label>
        <textarea class="form-control" id="body" name="body" rows="4" placeholder="请输入你的评价"></textarea>
      </div>
      <div class="mb-3">
        <input type="submit" name="submit" value="提交评价" class="btn btn-dark w-100">
      </div>
    </form>
    </div>
</main>

<footer class="text-center mt-5">
  版权所有 &copy; 2024
</footer>
 
<script src="https://cdn.bootcdn.net/ajax/libs/twitter-bootstrap/5.3.1/js/bootstrap.bundle.min.js"></script>

</body>
</html>

```

1. **`reviews.html`**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.1/css/bootstrap.min.css" rel="stylesheet">
  <title>课程评价</title>
</head>
<body>
  <nav class="navbar navbar-expand-sm navbar-light bg-light mb-4">
    <div class="container">
      <a class="navbar-brand" href="#">课程评价平台</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <a class="nav-link" href="./index.html">首页</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="./reviews.html">评价</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="./about.html">关于</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <main>
    <div class="container d-flex flex-column align-items-center">
      <h2>课程评价</h2>
      <div class="card my-3" style="width: 18rem;">
        <div class="card-body">
          这是一门非常实用的课程，深入浅出地介绍了编程基础。老师讲解清晰，配套资料丰富，非常推荐给编程新手。
        </div>
      </div>
      <div class="card my-3" style="width: 18rem;">
        <div class="card-body">
          我通过这门课程掌握了数据分析的核心技术，课程内容覆盖广泛，案例实战让我受益匪浅，值得一学。
        </div>
      </div>
      <div class="card my-3" style="width: 18rem;">
        <div class="card-body">
          作为一个设计背景的学生，这门课程帮我打开了前端开发的大门。课程结构合理，由浅入深，让我能够在短时间内构建出自己的网站。
        </div>
      </div>
    </div>
  </main>

  <footer class="text-center mt-5">
    版权所有 &copy; 2024
  </footer>

  <script src="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.1/js/bootstrap.bundle.min.js"></script>
</body>
</html>

```

1. **`about.html`**:

```html
<!DOCTYPE html>
<html lang="zh">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.1/css/bootstrap.min.css" rel="stylesheet">
  <title>关于我们</title>
</head>
<body>
  <nav class="navbar navbar-expand-sm navbar-light bg-light mb-4">
    <div class="container">
      <a class="navbar-brand" href="#">课程评价平台</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
         <li class="nav-item">
           <a class="nav-link" href="./index.html">首页</a>
         </li>
         <li class="nav-item">
           <a class="nav-link" href="./reviews.html">评价</a>
         </li>
         <li class="nav-item">
           <a class="nav-link" href="./about.html">关于</a>
         </li>
        </ul>
      </div>
  </div>
</nav>

<main>
  <div class="container d-flex flex-column align-items-center">
    <h2>关于我们</h2>

    <p class="text-center" style="max-width: 600px;">课程评价平台致力于为学生提供一个公正、开放的评价环境，帮助他们选择最合适的在线课程。我们相信，通过分享和交流课程体验，可以帮助每个人找到适合自己的学习路径。无论你是寻找提升技能的课程，还是想探索新领域的知识，这里都有丰富的资源等你发掘。</p>
    </div>
</main>

<footer class="text-center mt-5">
  版权所有 &copy; 2024
</footer>

<script src="https://cdn.bootcdn.net/ajax/libs/bootstrap/5.3.1/js/bootstrap.bundle.min.js"></script>

</body>
</html>

```

## 1. 配置PHP运行环境

1. **创建项目文件夹**: 在XAMPP目录下，找到**`htdocs`**文件夹。在**`htdocs`**中创建一个新的文件夹，命名为**`course-review-app`**。这个文件夹将用于存放你的项目文件。
2. **复制网页文件**: 将之前创建的静态网页文件（**`index.html`**, **`reviews.html`**, 和 **`about.html`**）复制到**`course-review-app`**文件夹中。
3. **启动Apache服务器**: 在XAMPP Control Panel中，找到Apache模块旁边的**`Start`**按钮，点击它启动Apache服务器。如果一切正常，你应该会看到Apache模块旁边的指示灯变为绿色。
4. **访问项目**: 打开Web浏览器，输入URL **`http://localhost/course-review-app/index.html`**。你应该能够看到你的**`index.html`**页面被正确渲染。

在浏览器中查看网页：

![Screenshot 2024-03-30 at 20.05.53.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.05.53.png)

![Screenshot 2024-03-30 at 20.06.34.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.06.34.png)

![Screenshot 2024-03-30 at 20.06.47.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.06.47.png)

## 2. 使用**`include`**引入PHP代码

### **1. 修改文件扩展名**

首先，需要将所有的**`.html`**文件（**`index.html`**、**`reviews.html`**、**`about.html`**）扩展名改为**`.php`**。这样做是因为我们即将在这些文件中引入PHP代码，而且Web服务器需要知道它们包含PHP代码，以便正确处理。

- **`index.html`** -> **`index.php`**
- **`reviews.html`** -> **`reviews.php`**
- **`about.html`** -> **`about.php`**

### **2. 创建`inc/`文件夹并添加PHP partial**

接下来，在项目目录中创建一个名为**`inc/`**的文件夹。这个文件夹将用来存放可重用的PHP片段，如网站的头部和尾部。这种做法可以避免在每个页面上重复相同的HTML代码，使得未来的维护和更新变得更加简单。

### **3. 创建`header.php`和`footer.php`**

在**`inc/`**文件夹中，创建两个PHP文件：**`header.php`**和**`footer.php`**。

- **`header.php`**: 包含网页的头部分（**`<head>`**标签、导航栏、开始的**`<main>`**标签），它将被包含在每个页面的顶部。
- **`footer.php`**: 包含关闭的**`<main>`**标签、网页的尾部内容（**`<footer>`**标签和引入的Bootstrap JavaScript文件），它将被包含在每个页面的底部。

将原始HTML文件中共通的头部和尾部HTML代码剪切到相应的**`header.php`**和**`footer.php`**文件中。

![Screenshot 2024-03-30 at 20.21.06.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.21.06.png)

![Screenshot 2024-03-30 at 20.22.24.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.22.24.png)

### **4. 在主页面中包含`header.php`和`footer.php`**

在**`index.php`**、**`reviews.php`**、和**`about.php`**中，使用PHP的**`include`**语句引入**`header.php`**和**`footer.php`**。例如，在**`index.php`**中：

```php
<?php include 'inc/header.php'; ?>
<!-- 页面的独特内容 -->
<?php include 'inc/footer.php'; ?>

```

![Screenshot 2024-03-30 at 20.27.04.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.27.04.png)

在`**reviews.php**`和`**about.php**`中也是一样：

![Screenshot 2024-03-30 at 20.31.25.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.31.25.png)

![Screenshot 2024-03-30 at 20.31.59.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.31.59.png)

通过以上步骤，你的项目结构现在支持PHP，并且通过使用**`include`**功能来重用代码，使得网站的开发和后续维护更加高效。每次修改头部或尾部时，只需要更新**`header.php`**或**`footer.php`**文件，变更就会自动应用到所有页面上。

对于你的PHP项目中的导航链接，我们需要做的是更新**`header.php`**文件中的链接路径，以确保在你的开发环境中它们能正确指向你的PHP页面。在我的截图中，项目位于**`/php-tutorial/course-review-app/`**。这意味着，为了从任何地方正确访问你的页面，你需要在链接中包含完整的路径，从服务器根目录开始，直到文件名。

### **5. 修改`header.php`中的链接**

打开**`header.php`**文件，并找到导航部分的HTML代码。你需要更新**`href`**属性，使其反映出你的项目在本地开发环境中的实际路径。

- 将**`href`**属性的值从**`./index.html`**改为**`/php-tutorial/course-review-app/index.php`**
- 类似地，更新**`reviews`**和**`about`**页面的链接。

![Screenshot 2024-03-30 at 20.43.29.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_20.43.29.png)

在修改了**`header.php`**文件后，由于你已经在所有页面（**`index.php`**, **`reviews.php`**, **`about.php`**）中包含了**`header.php`**，这些更改会自动反映在所有页面上。这展示了使用PHP **`include`**语句来重用代码部分的强大之处。

### **6. 测试网站导航**

- 通过在浏览器中访问你的项目（例如，通过输入**`http://localhost/php-tutorial/course-review-app/index.php`**）来测试更改。
- 点击所有导航链接，确保它们可以正确地将你从一个页面导航到另一个页面。
- 如果发现任何链接不工作，检查路径是否正确，确保路径正确匹配你的本地开发环境的目录结构。

![Untitled](assets/php-fundamentals-2/Untitled.png)

此时点击导航栏中的链接，他们应该都能正常导航。

## 3. 连接数据库测试&数组模拟数据

### **1. 创建`config/`文件夹和`db.php`**

- **`config/`**文件夹用于存放配置文件，如数据库连接信息。
- **`db.php`文件**：这个文件包含了定义数据库连接所需的信息（如数据库主机、用户名、密码和数据库名）和建立连接的代码。使用**`mysqli`**扩展来连接到MySQL数据库。
    
    ![Screenshot 2024-03-30 at 21.00.41.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.00.41.png)
    
💡 在编写PHP连接数据库的代码前，我们要先在MariaDB 中创建一个用户名、一个名为 **`review-app`** 的数据库，以及一个包含指定字段的表 **`review`**。

1. 创建用户名和赋予权限等

```sql
CREATE USER 'user_name'@'%' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON *.* TO 'user_name'@'%';
FLUSH PRIVILEGES;
```

1. **创建和选择数据库**：

```sql
CREATE DATABASE review_app;
USE review_app;
```

1. **创建表**：

```sql
CREATE TABLE review (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) NOT NULL,
  course_name VARCHAR(255) NOT NULL,
  content TEXT NOT NULL,
  date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

- **`id`**: 唯一标识每条评价的自增主键。
- **`name`**: 提交评价的用户的名字。
- **`email`**: 用户的电子邮件地址。
- **`course_name`**: 课程的名称。
- **`content`**: 评价的具体内容。
- **`date`**: 提交评价的日期和时间，默认为当前时间戳。
1. 插入数据：

```sql
INSERT INTO review (name, email, course_name, content) VALUES 
('张三', 'zhangsan@example.com', '计算机科学入门', '这门课程非常适合初学者，内容全面，讲解清晰。'),
('李四', 'lisi@example.com', '数据科学基础', '非常实用的课程，案例分析帮助我理解了数据科学的基本概念和应用。'),
('王五', 'wangwu@example.com', '前端开发入门', '课程内容丰富，涵盖了HTML、CSS和JavaScript，适合对前端开发感兴趣的人。'),
('赵六', 'zhaoliu@example.com', 'Python编程', '作为一个编程新手，这门课程帮助我打下了坚实的Python基础。');
```


### **2. 编写`db.php`的内容**

- **定义常量**：使用**`define`**函数定义数据库连接信息作为常量，这包括数据库主机（**`DB_HOST`**）、数据库用户名（**`DB_USER`**）、数据库密码（**`DB_PASS`**）和数据库名（**`DB_NAME`**）。
- **创建数据库连接**：使用**`new mysqli()`**创建一个新的数据库连接。这里传入之前定义的常量：主机名、用户名、密码、数据库名。
- **检查连接**：通过检查**`$conn->connect_error`**来确认是否成功连接到数据库。如果有错误，使用**`die()`**函数终止脚本并输出错误信息。
- **成功消息**：如果连接成功，打印出"连接成功！"消息。
    
    ![Screenshot 2024-03-30 at 21.02.34.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.02.34.png)
    

### **3. 更新`header.php`以包含`db.php`**

- 通过在**`header.php`**文件的开头包含**`db.php`**，你确保了每个使用了**`header.php`**的页面都能自动建立数据库连接。这是因为**`header.php`**被多个页面共享，因此是一个理想的位置来包含全局配置和初始化脚本。
- 在**`header.php`**的最开始，添加了**`<?php include 'config/db.php'; ?>`**。这行代码使用**`include`**语句引入**`db.php`**，使得数据库连接在**`header.php`**被引入的任何页面上自动建立。
    
    ![Screenshot 2024-03-30 at 21.03.09.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.03.09.png)
    
- 此时刷新网页，你将看到以下效果：
    
    ![Screenshot 2024-03-30 at 21.04.01.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.04.01.png)
    

测试完成后，可以在**`config/db.php`**文件中移除用于显示数据库连接成功消息的**`echo`**语句。

### **4. 在`reviews.php`中添加模拟数据**

在**`reviews.php`**文件中引入**`$reviews`**的PHP数组，该数组包含了三个评价的模拟数据。每个评价都是一个包含**`id`**、**`name`**、**`email`**、**`course_name`**、**`content`**和**`date`**键的关联数组。

这样做的目的是模拟从数据库获取的数据，以便在还没有实际连接数据库的情况下进行开发和测试。

### **5. 模拟数据的结构**

模拟数据的结构设计得非常类似于你可能从一个真实数据库表中检索到的数据结构。这包括了：

- **id**：唯一标识每个评价的数字。
- **name**：提交评价的用户的名字。
- **email**：用户的邮箱地址。
- **course_name**：评价的课程名称。
- **content**：评价内容。
- **date**：提交评价的日期和时间。

![Screenshot 2024-03-30 at 21.13.15.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.13.15.png)

### **6. 注释掉模拟数据**

先将**`$reviews`**数组中原有的三个模拟评价数据条目全部注释掉。

这相当于模拟一个从数据库中没有检索到任何评价的情况，或者是一个新网站刚刚上线还没有用户提交评价的场景。

### **7. 添加空数组检查逻辑**

接着，在显示评价的HTML标记之前加入了一个条件检查：

```php
<?php if(empty($reviews)): ?>
  <p class="lead mt3">目前没有课程评价！</p>
<?php endif; ?>
```

- **`empty($reviews)`**：这个PHP函数用来检查变量**`$reviews`**是否为空。如果你之前注释掉了所有模拟数据，那么**`$reviews`**这时应该是一个空数组。
- 如果**`$reviews`**为空，页面上将显示一条消息：“目前没有课程评价！”
- 使用Bootstrap的**`lead`**类和一个**`mt3`**（用于调整上边距）来格式化显示的消息，使其更符合整体网站风格。

![Screenshot 2024-03-30 at 21.17.52.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.17.52.png)

此时的网页显示效果：

![Untitled](assets/php-fundamentals-2/Untitled%201.png)

### **8. 重新启用模拟数据**

取消之前对模拟数据的注释，使得**`$reviews`**数组再次包含了三个评价的数据。

### **9. 删除网页模版代码**

接下来，删除**`reviews.php`**中的硬编码HTML模板代码，这部分代码是一些静态的评价卡片示例。

<aside>
💡 在实际开发过程中，这些静态内容通常用作开发和设计的初期占位符，以便在没有实际数据时展示页面的大致布局。通过删除这些静态内容，并准备使用PHP动态生成内容，你的页面现在将能够根据**`$reviews`**数组中的数据动态展示评价信息。

</aside>

![Screenshot 2024-03-30 at 21.23.30.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.23.30.png)

此时你的评价网页应该只剩下一个卡片：

![Screenshot 2024-03-30 at 21.26.50.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.26.50.png)

### **10. 使用`foreach`循环遍历评价数据**

该循环遍历**`$reviews`**数组，并为数组中的每个元素（即每条评价）生成一段HTML标记。

这是动态内容生成的关键步骤，它允许页面根据**`$reviews`**数组的内容自动更新评价信息。

```php
<?php foreach($reviews as $review):?>
  <div class="card my-3" style="width: 18rem;">
    <div class="card-body">
      这是一门非常实用的课程，深入浅出地介绍了编程基础。老师讲解清晰，配套资料丰富，非常推荐给编程新手。
    </div>
  </div>
<?php endforeach; ?>

```

![Screenshot 2024-03-30 at 21.30.03.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.30.03.png)

此时评价页效果如下：

![Screenshot 2024-03-30 at 21.30.44.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.30.44.png)

### **11. 动态显示评价内容**

修改**`foreach`**循环中的HTML代码，以确保评价卡片现在展示的是数组**`$reviews`**中每个评价具体的内容，而不再是之前的静态文本。这是通过从**`$review`**变量中动态获取评价内容(**`content`**)来实现的。

![Screenshot 2024-03-30 at 21.35.55.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.35.55.png)

此时评价页效果如下：

![Screenshot 2024-03-30 at 21.37.06.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.37.06.png)

### **12. 完善评价卡片的内容**

扩展评价卡片的结构，以包括以下几个部分：

1. **课程名称**：作为**`card-title`**，现在以文本居中的形式显示在卡片的顶部，通过**`<?php echo $review['course_name']; ?>`**动态获取和显示。
2. **评价内容**：评价内容现在被引号**`“”`**包裹，增加了阅读体验的美感，依然通过**`<?php echo $review['content']; ?>`**来动态展示。
3. **评价者名称**：在评价内容的下方，添加了一个文本**`来自 <?php echo $review['name'];?>`**，动态显示评价者的名字，以及一个**`text-secondary`**类来设置文本颜色，以区分评价内容和评价者。

![Screenshot 2024-03-30 at 21.40.07.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.40.07.png)

此时网页效果：

![Screenshot 2024-03-30 at 21.40.26.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.40.26.png)

## 4. 从数据库中获得真实数据

### **1. 移除模拟数据数组**

删除原来用于存储评价信息的静态PHP数组**`$reviews`**。这个数组之前包含了手动输入的评价数据，用于在页面上展示评价信息。

### **2. 引入数据库查询逻辑**

接着，添加新的PHP代码来从数据库中查询评价数据：

```php
$sql = 'SELECT * FROM review';
$result = mysqli_query($conn, $sql);
$reviews = mysqli_fetch_all($result, MYSQLI_ASSOC);
```

这里的代码执行了以下操作：

1. **定义SQL查询**：通过**`$sql = 'SELECT * FROM review';`**定义了一个SQL查询，其目的是从名为**`review`**的数据库表中选择所有列的数据。
2. **执行查询**：使用**`mysqli_query($conn, $sql);`**执行上面定义的SQL查询。这里，**`$conn`**是一个已经通过**`db.php`**文件建立的数据库连接对象。
3. **获取结果**：通过**`mysqli_fetch_all($result, MYSQLI_ASSOC);`**获取查询结果，并将其作为一个关联数组存储在**`$reviews`**变量中。**`MYSQLI_ASSOC`**参数确保了结果数组以关联数组的形式返回，其中数组的键是数据库表列的名称。

![Screenshot 2024-03-30 at 21.56.37.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.56.37.png)

此时评价页的网页效果应如下，显示的内容来自数据库：

![Screenshot 2024-03-30 at 21.57.10.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_21.57.10.png)

### **3. 在评价卡片中显示日期**

为每个评价卡片添加了一个显示评价日期的部分。

这是通过向现有的HTML结构中添加以下代码实现的：

```php
<div class="text-secondary mt-2">
  <?php echo $review['date'];?>
</div>
```

通过**`<?php echo $review['date'];?>`**动态地插入了评价的日期。这个日期是从数据库中获取的，作为评价数据的一部分存储在**`$review`**数组的**`date`**键中。

此时的评价页如下所示：

![Screenshot 2024-03-30 at 22.00.41.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.00.41.png)

## 5. 主页表单处理

### **1. 初始化表单变量**

在**`index.php`**的顶部添加一段PHP代码，用于初始化表单数据和错误消息的变量：

```php
<?php
  $name = $email = $courseName = $content = '';
  $nameErr = $emailErr = $courseNameErr = $contentErr = '';
?>
```

![Screenshot 2024-03-30 at 22.08.15.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.08.15.png)

这里，每个表单字段（如姓名、邮箱、课程名称和评价内容）都有对应的两个变量：

1. **数据变量**（**`$name`**, **`$email`**, **`$courseName`**, **`$content`**）：用于存储用户通过表单提交的数据。初始化为空字符串**`''`**，这意味着在表单首次加载时，这些字段将为空。
2. **错误消息变量**（**`$nameErr`**, **`$emailErr`**, **`$courseNameErr`**, **`$contentErr`**）：用于存储与每个表单字段相关的错误消息。如果用户提交的数据不满足特定的验证条件（如必填字段为空、格式错误等），相应的错误消息变量将被填充，以便在表单旁边显示错误消息。这些变量同样被初始化为空字符串**`''`**。

### **2. 修改表单的`action`属性和`method`属性**

更改表单的提交行为：

- **`action`属性**：现在使用**`<?php echo htmlspecialchars($_SERVER['PHP_SELF']) ?>`**动态设置为当前脚本的路径。这意味着表单将会提交到和表单相同的PHP文件（即**`index.php`**）上。**`htmlspecialchars()`**函数确保输出是安全的，避免XSS攻击。
- **`method`属性**：设置为**`"POST"`**，这表明表单数据将通过HTTP POST方法发送。与GET方法相比，POST更适合于提交表单数据，尤其是包含敏感信息（如用户个人信息）的情况，因为POST请求的数据不会显示在URL中。

### **3. 准备处理表单提交的PHP代码**

在PHP代码块中添加了一个检查，以确定表单是否被提交：

```php
if (isset($_POST['submit'])) {

}
```

- 使用**`isset($_POST['submit'])`**检查表单是否通过点击提交按钮而提交。这里，**`submit`**是你将要为提交按钮指定的**`name`**属性值，这个检查确定了是否有数据需要处理。

![Screenshot 2024-03-30 at 22.10.55.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.10.55.png)

### **4. 验证姓名字段**

当用户提交表单时，通过PHP代码来验证姓名字段是否已被填写：

1. **检查姓名字段是否为空**：
使用**`empty($_POST['name'])`**来检查用户是否在姓名字段中输入了值。如果此字段为空，表示用户没有输入姓名，这时会设置**`$nameErr`**变量为错误消息**`"姓名为必填项！"`**。这个错误消息可以在表单旁边显示，提示用户需要填写姓名。
2. **处理非空姓名输入**：
如果姓名字段不为空，则使用**`filter_input(INPUT_POST, 'name', FILTER_SANITIZE_FULL_SPECIAL_CHARS)`**来获取并清理姓名字段的值。这里，**`FILTER_SANITIZE_FULL_SPECIAL_CHARS`**过滤器会删除或编码特殊字符，这是一种防范XSS（跨站脚本）攻击的常用手段。经过处理后，姓名字段的值被安全地存储在**`$name`**变量中，以备后续使用。

![Screenshot 2024-03-30 at 22.14.06.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.14.06.png)

### **5. 验证邮箱字段**

就像之前对姓名字段所做的那样，现在对邮箱字段也实施了验证：

1. **检查邮箱字段是否为空**：
首先，使用**`empty($_POST['email'])`**来检查用户是否在邮箱字段中输入了值。如果此字段为空，表示用户没有输入邮箱，这时会设置**`$emailErr`**变量为错误消息**`"邮箱为必填项！"`**。
2. **处理非空邮箱输入**：
如果邮箱字段不为空，则使用**`filter_input(INPUT_POST, 'email', FILTER_SANITIZE_FULL_SPECIAL_CHARS)`**来获取并清理邮箱字段的值。同样，这里的过滤器会删除或编码特殊字符，防范潜在的XSS攻击，并将处理后的值存储在**`$email`**变量中。

### **6. 输出验证结果到网页**

在进行了姓名和邮箱的验证之后，你通过简单的**`echo`**语句将姓名的错误信息（如果有的话）和用户输入的姓名（如果验证通过的话）输出到了网页上：

```php
echo $nameErr;
echo $name;
```

![Screenshot 2024-03-30 at 22.19.41.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.19.41.png)

此时的主页效果，但你不输入姓名项直接提交时，它将显示提示：

![Untitled](assets/php-fundamentals-2/Untitled%202.png)

### **7. 移除输出语句&`is-invalid`类**

移除之前用于直接在页面上显示姓名字段验证结果的**`echo`**语句。

更新**`index.php`**中姓名输入字段的HTML标记，为其添加了Bootstrap的**`is-invalid`**类。

这个类用于视觉上标记表单控件的验证状态，当输入不满足验证条件（比如，字段为空）时，Bootstrap会以红色边框或其他错误提示的方式高亮显示该控件。

![Screenshot 2024-03-30 at 22.27.41.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.27.41.png)

此时的主页效果，当你无姓名内容点击提交时：

![Screenshot 2024-03-30 at 22.28.32.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.28.32.png)

### **8. 条件渲染`is-invalid`类**

修改姓名输入字段的**`class`**属性，使其能够根据**`$nameErr`**变量的值动态添加**`is-invalid`**类。

如果**`$nameErr`**变量包含错误消息（即非空），则**`is-invalid`**类将被添加到**`class`**列表中，否则不添加任何内容。

更新的代码如下：

```php
<input type="text" class="form-control <?php echo $nameErr ? 'is-invalid' : null; ?>" id="name" name="name" placeholder="请输入你的姓名">
```

这种方式使得只有在验证失败时，输入字段才会以视觉上突出的方式（如红色边框）标记为无效，提供即时的视觉反馈给用户。

### **9. 显示具体的错误消息**

除了动态添加**`is-invalid`**类外，还需要引入了一个新的**`div`**元素，用于显示具体的错误消息。这个**`div`**具有Bootstrap的**`invalid-feedback`**类，它被设计用来在表单控件被标记为无效时显示错误消息。

添加的代码如下：

```php
<div class="invalid-feedback">
  <?php echo $nameErr; ?>
</div>
```

当**`$nameErr`**变量包含错误消息时，这条消息将在对应的输入字段下方以红色文本显示，进一步提升了用户的错误识别和修正效率。

![Screenshot 2024-03-30 at 22.32.18.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.32.18.png)

此时主页的效果：

![Screenshot 2024-03-30 at 22.33.12.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.33.12.png)

### 10. 验证各个字段

下一步对**`index.php`**进行了进一步的更新，扩展了表单验证逻辑以包括课程名称和评价内容的验证，并且为每个字段添加了条件渲染的错误提示样式。

![Screenshot 2024-03-30 at 22.38.12.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.38.12.png)

![Screenshot 2024-03-30 at 22.38.32.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.38.32.png)

此时当你试图提交空字段的话，点击提交时将会显示（课程名称那里有BUG，在下一步修复）：

![Screenshot 2024-03-30 at 22.39.14.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.39.14.png)

### **11. 提交数据到数据库**

先修正之前的一个变量名错误：将**`$couseName`**更正为**`$courseName`**。

接下来，增加一段新的PHP代码，用于在所有输入字段通过验证（即没有错误消息）的情况下，将表单数据插入到数据库中：

```php
if (empty($nameErr) && empty($emailErr) && empty($courseNameErr) && empty($contentErr)) {
  // 添加到数据库
  $sql = "INSERT INTO review (name, email, course_name, content) VALUES('$name', '$email', '$courseName', '$content')";

  if (mysqli_query($conn, $sql)) {
    // 成功
    header('Location: reviews.php');
  } else {
    // 错误
    echo "出错：" . mysqli_error($conn);
  }
}
```

这段代码首先检查是否有任何验证错误，如果所有的**`$nameErr`**、**`$emailErr`**、**`$courseNameErr`**和**`$contentErr`**变量都为空，表示表单的所有字段都通过了验证。然后，它构造了一个SQL插入语句，用于将用户输入的姓名、邮箱、课程名称和评价内容添加到**`review`**数据库表中。

使用**`mysqli_query()`**函数执行这个SQL语句，如果插入成功，将通过**`header('Location: reviews.php');`**重定向用户到**`reviews.php`**页面，这通常用于提示用户操作成功，并展示所有评价。如果发生错误，则通过**`echo "出错：" . mysqli_error($conn);`**输出错误信息，供调试使用。

此时你的主页应该可以提交表单内容到数据库：

![Screenshot 2024-03-30 at 22.44.35.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.44.35.png)

提交后：

![Untitled](assets/php-fundamentals-2/Untitled%203.png)

### **12. 更新图片链接**

在**`index.php`**文件中，更新指向logo图片的路径，因为我发现我一直没有打对图片的路径🤡。

![Screenshot 2024-03-30 at 22.49.24.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.49.24.png)

此时主页效果：

![Screenshot 2024-03-30 at 22.49.48.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.49.48.png)

### **13. 移除冗余元素**

从**`about.php`**页面中移除了以下两个元素：

1. **`<div class="container">`**：这个**`<div>`**标签是之前用于包裹页面内容的容器。考虑到**`header.php`**中已经包含了容器元素，这里的容器是多余的，因此要将其删除。
2. **`<a class="navbar-brand" href="#">课程评价平台</a>`**：这个链接是在导航栏中重复显示了平台的名称。由于在**`header.php`**中通常会包含导航栏和平台品牌信息，因此在**`about.php`**页面上再次添加这个元素是不必要的。

![Screenshot 2024-03-30 at 22.52.40.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.52.40.png)

此时的关于页如下：

![Screenshot 2024-03-30 at 22.52.58.png](assets/php-fundamentals-2/Screenshot_2024-03-30_at_22.52.58.png)

# 实验要求：**构建课程评价应用**

### 实验目的

本实验旨在通过构建一个简单的课程评价应用，使学生熟悉Web开发的基础知识，包括前端和后端的基本概念，同时学习使用Git作为版本控制工具和Gitee作为代码托管平台的实践操作。

### 实验内容

1. **环境准备**：
    - 安装并配置Apache服务器、PHP、MySQL（使用XAMPP）。
    - 安装Git，并配置Git的本地用户名和邮箱（确保每次提交使用相同的用户名和邮箱）。
    - 注册Gitee账号，并创建新的公开仓库“课程评价APP”。
2. **项目实现与提交记录**：
    - 按照指导书的步骤，从项目的初始化到功能的逐步实现，完成课程评价应用的开发。
    - 使用Git进行版本控制，记录至少10条关键的提交（commit），每次提交应准确反映所完成的功能或所做的更改。
    - 提交信息（commit message）应清晰说明所做的更改。
3. **推送到Gitee**：
    - 将本地的代码仓库推送到Gitee上新建的“课程评价APP”仓库中。
    - 确保仓库中的代码是最新的，并且包含所有的提交记录。
4. **提交内容**：
    - 在学习通上提交以下内容：
        - 你的Gitee账号的个人主页链接。
        - “课程评价APP”仓库的地址（应以.git结尾的链接）。