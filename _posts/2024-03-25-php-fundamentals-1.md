---
layout: post
title: "PHP基本语法1"
date: 2024-03-25 15:01:34 -0700
categories: php
---

# PHP简介

PHP（超文本预处理器）是一种广泛使用的开源服务器端脚本语言，特别适用于Web开发并可嵌入HTML中。它最初被创建于1994年，由Rasmus Lerdorf开发。PHP的主要特点包括：

1. **服务器端执行**：PHP代码在服务器上执行，然后将生成的HTML发送给客户端浏览器。这意味着PHP代码不会暴露给客户端，增加了开发的安全性。
2. **灵活性**：PHP可以嵌入到HTML代码中，也可以与多种数据库（如MySQL, PostgreSQL, Oracle等）交互，非常适合动态网页和应用程序开发。
3. **广泛的应用**：PHP用于创建各种Web应用，从小型个人博客到大型企业级网站。著名的内容管理系统（CMS），如WordPress和Joomla，也是用PHP开发的。
4. **易于学习**：对于初学者来说，PHP是一个学起来相对容易的语言，拥有大量的学习资源和社区支持。

# 设置环境（XAMPP）

XAMPP是一个流行的PHP开发环境，包括Apache、MySQL、PHP和Perl。它是搭建PHP开发环境的最简单方法。

1. **下载和安装XAMPP**：
    - 访问 [XAMPP的官网](https://www.apachefriends.org/index.html) 并下载适合你操作系统的版本。
    - 安装XAMPP，过程中可以选择需要安装的组件（确保包括Apache和PHP）。
2. **启动XAMPP**：
    - 安装完成后，打开XAMPP控制面板。
    - 启动Apache服务（如果需要MySQL，也启动MySQL服务）。
3. **测试PHP**：
    - 在XAMPP的主目录下找到**`htdocs`**文件夹。
    
    ![Untitled](assets/php-fundamentals-1/Untitled.png)
    
    - 在**`htdocs`**中创建一个`**php-tutorial**`文件夹，并在里面创建**`index.php`**，并写入一些PHP代码，如：
    
    ![Untitled](assets/php-fundamentals-1/Untitled%201.png)
    
    - 在浏览器中访问 **`http://localhost/php-tutorial`**，如图所示：
    
    ![Untitled](assets/php-fundamentals-1/Untitled%202.png)
    

<aside>
💡 PHP试验推荐使用Visual Studio Code插件：

- Live Server
- PHP Intelephense
</aside>

# 各种输出

在php文件中可以使用html元素标签，比如：

![Untitled](assets/php-fundamentals-1/Untitled%203.png)

![Untitled](assets/php-fundamentals-1/Untitled%204.png)

**`.php`**代码文件一般以以下标签开头：

```php
<?php 

?> // 如果下面没有html或其他内容的php，我们其实不需要此关闭php标签。
```

<aside>
💡 推荐在开发过程中，通过以下方法设置在网页中显示错误信息：

1. 去到XAMPP的主目录下，打开**`etc/`**文件夹，编辑**`php.ini`**文件，搜索**`display_errors`**设置为**`on`**。如图：

![Untitled](assets/php-fundamentals-1/Untitled%205.png)

1. **或**将以下代码放在PHP脚本的开始处，可以使得所有错误和警告信息都会显示在网页上：
    
    ```php
    ini_set('display_errors', 1);
    error_reporting(E_ALL);
    ```
    
2. 这在调试中非常有用，但要记得在生产环境中关闭错误显示，以免泄露敏感信息。
</aside>

打开网页的错误报告后，当代码有语法错误，相关信息将显示在网页上。比如，如果`php`标签没有结尾，而下方又有**`html`**代码时：

![Untitled](assets/php-fundamentals-1/Untitled%206.png)

错误信息会显示在网页中：

![Untitled](assets/php-fundamentals-1/Untitled%207.png)

在PHP中我们有以下方法用于输出数据：

1. **echo**：用于输出字符串、数字、HTML等。这是PHP中最常用的输出语句之一。它可以很快地输出一个或多个值。示例中首先输出了字符串**`'Hello'`**，然后输出数字**`123`**，最后输出一个HTML标签。
    
    ```php
    echo 'Hello';
    echo 123;
    echo '<h1>Hello</h1>';
    
    ```
    
2. **print**：与**`echo`**相似，也是用于输出的，但它略慢一些。**`print`**只能输出一个值，并且总是返回1。这意味着它可以用在表达式中。
    
    ```php
    print 'Hello';
    
    ```
    
3. **print_r**：用于输出更多信息，常用于打印数组。对于字符串，**`print_r`**的输出与**`echo`**和**`print`**类似。但是当输出数组时，它会显示数组的结构，这对于调试很有帮助。
    
    ```php
    print_r('Hello');
    print_r([1, 2, 3]);
    
    ```
    
4. **var_dump**：提供了更多的信息，包括数据的类型和长度。对于复杂数据类型（如数组），**`var_dump`**能够输出更详细的信息，包括数组内的每个元素及其类型。这在调试时非常有用，尤其是当需要知道变量的确切类型和结构时。
    
    ```php
    var_dump('Hello');
    var_dump([1, 2, 3]);
    
    ```
    

比如：

![Untitled](assets/php-fundamentals-1/Untitled%208.png)

![Untitled](assets/php-fundamentals-1/Untitled%209.png)

![Untitled](assets/php-fundamentals-1/Untitled%2010.png)

![Untitled](assets/php-fundamentals-1/Untitled%2011.png)

其中，使用**`echo`**语句可以输出输出字符串、数字、HTML，但输出数组时会出现警告：

![Untitled](assets/php-fundamentals-1/Untitled%2012.png)

![Untitled](assets/php-fundamentals-1/Untitled%2013.png)

我们可以使用**`implode()`**方法将数组转化为字符串：

<aside>
💡 **`implode()`** 是 PHP 中的一个函数，用于将数组元素组合成一个字符串。

### **语法**

```php
string implode ( string $separator , array $array )
```

- **`$separator`**：分隔符，用于在数组元素之间插入。如果你不想在元素之间有任何分隔符，可以使用空字符串(**`''`**)作为分隔符。
- **`$array`**：要合并成字符串的数组。
</aside>

比如：

![Untitled](assets/php-fundamentals-1/Untitled%2014.png)

![Untitled](assets/php-fundamentals-1/Untitled%2015.png)

使用其他的输出方法：

![Untitled](assets/php-fundamentals-1/Untitled%2016.png)

你还可以在php文件中嵌入HTML和PHP代码，在 HTML 中输出 PHP 变量或表达式的结果。比如：

![Untitled](assets/php-fundamentals-1/Untitled%2017.png)

![Untitled](assets/php-fundamentals-1/Untitled%2018.png)

还可以这样简写，效果是一样的：

![Untitled](assets/php-fundamentals-1/Untitled%2019.png)

<aside>
💡 PHP 代码块中的语句通常以分号 (**`;`**) 结束。但在代码块的最后一个语句后，如果紧跟着 PHP 的结束标签 **`?>`**，那么这个分号可以省略。

</aside>

<aside>
💡 在PHP文件中使用注释的方法如下：

```php
/* ------------ 注释 ------------ */

// 单行注释

/*
      * 多行注释
      * 多行注释
      * 多行注释
*/
```

</aside>

# 变量

我们先整理一下PHP实验的文件，将**`index.php`**文件命名为**`01_output.php`，**并打开浏览器，重新访问**`localhost/php-tutorial`**，内容显示应如下：

![Untitled](assets/php-fundamentals-1/Untitled%2020.png)

在**`php-tutorial`**文件夹下新建**`02_variables.php`**文件，后续的实验将延续这种文件命名风格：

![Untitled](assets/php-fundamentals-1/Untitled%2021.png)

在 PHP 中，变量是存储信息的容器，可以包含各种数据类型的值，比如字符串、整数、浮点数、布尔值、数组、对象、NULL 和资源。这些注释提供了关于 PHP 数据类型和变量命名规则的基本概述。

**PHP 数据类型**

- **String（字符串）**：由字符组成，必须被引号包围，可以是单引号或双引号。
- **Integer（整数）**：没有小数的数字。
- **Float（浮点数）**：有小数点的数字，也称为双精度数。
- **Boolean（布尔值）**：只有两个值，**`true`** 或 **`false`**，用于条件判断。
- **Array（数组）**：可以存储多个值的特殊变量，这些值可以是不同数据类型。
- **Object（对象）**：基于类的实例，用于面向对象编程。
- **NULL（空）**：代表没有任何值的变量。
- **Resource（资源）**：用来保存外部资源的特殊变量，比如数据库连接。

**变量命名规则**

- 变量名必须以美元符号（**`$`**）开头。
- 变量名的第一个字符必须是字母（A-z）或下划线（**`_`**）。
- 变量名不能以数字开头。
- 变量名只能包含字母、数字和下划线（**`A-z`**、**`0-9`**、**`_`**）。
- 变量名是区分大小写的，因此**`$name`**和**`$NAME`**被认为是两个不同的变量。

比如以下的例子：

![Untitled](assets/php-fundamentals-1/Untitled%2022.png)

![Untitled](assets/php-fundamentals-1/Untitled%2023.png)

![Untitled](assets/php-fundamentals-1/Untitled%2024.png)

![Untitled](assets/php-fundamentals-1/Untitled%2025.png)

接下来，我们来看看在 PHP 中如何将变量添加到字符串中，以及如何拼接字符串。

在双引号（**`"`**）中直接引用变量：当字符串被双引号包围时，可以直接在字符串内部插入变量，PHP 会解析这些变量并将它们的值嵌入到字符串中。例如，**`echo "$name 的年龄是 $age 岁";`** 中的 **`$name`** 和 **`$age`** 会被它们各自的值所替换。

![Untitled](assets/php-fundamentals-1/Untitled%2026.png)

![Untitled](assets/php-fundamentals-1/Untitled%2027.png)

使用点（**`.`**）操作符拼接字符串和变量：这种方法涉及到使用点（**`.`**）操作符将字符串字面量和变量连接起来，形成一个新的字符串。例如，**`echo . $name . " 的年龄是 " . $age . " 岁";`**。

![Untitled](assets/php-fundamentals-1/Untitled%2028.png)

使用花括号（**`{}`**）来明确变量的边界：这种方法使得变量的界限更加清晰，尤其是在变量名周围可能存在歧义的字符时。例如，**`echo "${name} 的年龄是 ${age} 岁";`**

![Untitled](assets/php-fundamentals-1/Untitled%2029.png)

接下来，我们看看在 PHP 中使用算术运算符进行基本的数学运算。

在 PHP 中，算术运算符包括加法 (**`+`**)、减法 (**`-`**)、乘法 (**`*`**) 和除法 (**`/`**)，可以对数值进行操作并返回结果。下面是每个运算符的具体用法：

1. **加法 (`+`)**: 将两个数值相加。
    
    ```php
    echo 5 + 5; // 输出 10
    ```
    
    这里将 5 和 5 相加，结果是 10。
    
2. **减法 (``)**: 从一个数值中减去另一个数值。
    
    ```php
    echo 10 - 5; // 输出 5
    ```
    
    这里从 10 中减去 6，结果是 4。
    
3. **乘法 (``)**: 将两个数值相乘。
    
    ```php
    echo 5 * 6; // 输出 30
    ```
    
    这里将 5 和 10 相乘，结果是 50。
    
4. **除法 (`/`)**: 用一个数值除以另一个数值。
    
    ```php
    echo 10 / 2; // 输出 5
    ```
    
    这里将 10 除以 2，结果是 5。
    

比如：

![Untitled](assets/php-fundamentals-1/Untitled%2030.png)

此时结果：

![Untitled](assets/php-fundamentals-1/Untitled%2031.png)

接下来，我们来看看如何在 PHP 中定义和使用常量。常量是在脚本执行期间不会改变的值。

在编程中，常量被用于存储不需要改变的值，例如配置信息（如数据库连接信息）、路径名、特定的重要数值等。

比如：

![Untitled](assets/php-fundamentals-1/Untitled%2032.png)

# 数组

PHP中的数组是一种复合数据类型，可以存储多个值。数组中的每个值可以通过索引访问，并且可以包含不同类型的数据（如字符串、整数和对象）。PHP支持数值数组和关联数组两种主要类型的数组：

### **数值数组（Indexed Arrays）**

数值数组使用数字作为索引。这些索引默认从0开始自动分配，但你也可以手动指定索引。

```php
$fruits = array("Apple", "Banana", "Cherry");
// 或使用简短语法
$fruits = ["Apple", "Banana", "Cherry"];
```

在上面的例子中，**`$fruits[0]`** 会返回 "Apple"。

### **关联数组（Associative Arrays）**

关联数组使用你分配给数组的每个元素的键（字符串）作为索引。这对于存储键值对非常有用。

```php
$age = array("Peter" => "35", "Ben" => "37", "Joe" => "43");
// 或使用简短语法
$age = ["Peter" => "35", "Ben" => "37", "Joe" => "43"];
```

在这个例子中，**`$age["Ben"]`** 会返回 "37"。

### **多维数组**

PHP也支持多维数组，即数组中的元素也可以是另一个数组。这对于表示更复杂的数据结构，如矩阵或数据库查询结果，非常有用。

```php
$contacts = array(
    array(
        "name" => "Peter Parker",
        "email" => "peterparker@mail.com",
    ),
    array(
        "name" => "Clark Kent",
        "email" => "clarkkent@mail.com",
    ),
);
```

在上面的例子中，**`$contacts[0]["name"]`** 会返回 "Peter Parker"。

比如我们来看以下的例子：

![Untitled](assets/php-fundamentals-1/Untitled%2033.png)

![Untitled](assets/php-fundamentals-1/Untitled%2034.png)

![Untitled](assets/php-fundamentals-1/Untitled%2035.png)

![Untitled](assets/php-fundamentals-1/Untitled%2036.png)

![Untitled](assets/php-fundamentals-1/Untitled%2037.png)

![Untitled](assets/php-fundamentals-1/Untitled%2038.png)

比如，我们来创建一个名为**`$person`**的关联数组，其中包含了三个键值对：

- **`'first_name' => 'Hings'`**：这一行定义了一个键**`'first_name'`**，其对应的值是字符串**`'Hings'`**。这表示人的名字。
- **`'last_name' => 'Li'`**：这一行定义了一个键**`'last_name'`**，其对应的值是字符串**`'Li'`**。这表示人的姓氏。
- **`'email' => 'hings@gmail.com'`**：这一行定义了一个键**`'email'`**，其对应的值是字符串**`'hings@gmail.com'`**。这表示人的电子邮件地址。

关联数组是一种非常有用的数据结构，可以通过键（通常是字符串）来存储和访问数据。在这个例子中，**`$person`**数组可以用来存储和组织关于一个人的信息，如名字、姓氏和电子邮件地址。你可以通过键名来访问数组中的特定信息，例如**`$person['first_name']`**将返回**`'Hings'`**。

![Untitled](assets/php-fundamentals-1/Untitled%2039.png)

![Untitled](assets/php-fundamentals-1/Untitled%2040.png)

有比如，我们来定义了一个名为**`$people`**的数组，其中包含了多个人的信息。

这个数组是一个多维关联数组，每个元素本身也是一个关联数组，存储着个人的信息（如名字、姓氏和电子邮件地址）。

- **`$person`**：这是**`$people`**数组的第一个元素。假设之前已经定义了一个关联数组**`$person`**（如前一个例子所示），这里将其作为**`$people`**数组的一个元素。因此，**`$person`**数组的所有键值对（**`first_name`**、**`last_name`**、**`email`**）都会被包含在**`$people`**数组的这个位置。
- 第二个元素是一个直接在**`$people`**数组内部定义的关联数组，包含了**`'first_name' => 'John'`**、**`'last_name' => 'Doe'`**、**`'email' => 'john@gmail.com'`**这些键值对。
- 第三个元素也是一个关联数组，包含了**`'first_name' => 'Jane'`**、**`'last_name' => 'Doe'`**、**`'email' => 'jane@gmail.com'`**这些键值对。

![Untitled](assets/php-fundamentals-1/Untitled%2041.png)

![Untitled](assets/php-fundamentals-1/Untitled%2042.png)

我们可以这样访问多维数组的值：

![Untitled](assets/php-fundamentals-1/Untitled%2043.png)

此时效果：

![Untitled](assets/php-fundamentals-1/Untitled%2044.png)

接下来使用**`json_encode()`**函数将**`$people`**数组转换成JSON格式的字符串，并通过**`var_dump()`**函数输出转换结果的详细信息。

**`json_encode()`**是PHP中的一个函数，用于将PHP数组（或对象）转换为JSON格式的字符串。这对于Web应用程序中的数据交换非常有用，比如发送数据到客户端JavaScript，或者通过API与其他应用程序交互。

![Untitled](assets/php-fundamentals-1/Untitled%2045.png)

输出结果：

![Untitled](assets/php-fundamentals-1/Untitled%2046.png)

我们来看看如何使用 PHP 中的 **`json_decode()`** 函数将 JSON 格式的字符串解码转换成 PHP 对象或数组。

**`json_decode()`** 是 PHP 中的一个函数，用于将 JSON 格式的字符串解码（转换）为 PHP 变量。默认情况下，这个函数将 JSON 对象转换为 PHP 对象。如果你想将 JSON 对象转换为 PHP 关联数组，可以将 **`json_decode()`** 函数的第二个参数设置为 **`true`**。

![Untitled](assets/php-fundamentals-1/Untitled%2047.png)

输出结果：

![Untitled](assets/php-fundamentals-1/Untitled%2048.png)

# 条件判断

### **运算符**

在PHP中，条件判断通常依赖于比较运算符来比较两个值，根据比较结果（真或假）来决定执行哪部分代码。这里列出的运算符包括：

- **`<`** 小于
- **`>`** 大于
- **`<=`** 小于或等于
- **`>=`** 大于或等于
- **`==`** 等于（值相等，不考虑类型）
- **`===`** 全等于（值和类型都相等）
- **`!=`** 不等于（值不相等，不考虑类型）
- **`!==`** 不全等（值不相等，或类型不相等）

### **If语句**

**`if`**语句是基本的条件判断结构，允许根据条件的真假来执行不同的代码块。

```php
if (condition) {
  // 如果条件为真，则执行这里的代码
}
```

- **`condition`**：这里是要评估的表达式，其结果会被解释为布尔值（真或假）。如果条件为真（即表达式的结果为**`true`**），则执行大括号**`{}`**中的代码。

比如：

![Untitled](assets/php-fundamentals-1/Untitled%2049.png)

在这个示例中，条件**`$age >= 18`**判断年龄是否大于或等于18。如果条件为真（即年龄大于或等于18岁），则执行**`if`**语句内的代码，输出"你成年了！"。

我们来看下一个例子，在这个例子中：

1. 首先，使用**`date('H')`**函数获取当前的小时数（24小时制）。这个值被赋给变量**`$t`**。
2. 接下来，通过**`if`**语句判断当前时间，并根据时间的不同范围显示相应的问候语：
    - 如果**`$t < 12`**（即当前时间小于12小时），代码会输出"早上好！"。
    - 如果当前时间不小于12小时但**`$t < 17`**（即当前时间在12到16小时之间），代码会输出"下午好！"。
    - 如果上述条件都不满足（即当前时间大于或等于17小时），代码会输出"晚上好！"。

![Untitled](assets/php-fundamentals-1/Untitled%2050.png)

![Untitled](assets/php-fundamentals-1/Untitled%2051.png)

我们来看下一个例子，

- 在这个例子中使用**`empty($posts[0])`**来检查**`$posts`**数组的第一个元素是否存在且非空。
- 如果**`$posts`**数组的第一个元素存在且非空，就输出这个元素的值。
- 如果不满足上述条件（即数组为空或第一个元素为空），则输出"根本没有帖子！"。

![Untitled](assets/php-fundamentals-1/Untitled%2052.png)

![Untitled](assets/php-fundamentals-1/Untitled%2053.png)

我们还可以使用三元运算符，比如：

- **`echo !empty($posts[0]) ? $posts[0] : "根本没有帖子";`** 这行代码使用了条件（三元）运算符来检查**`$posts[0]`**是否非空。如果是，就输出**`$posts[0]`**的值；如果不是，就输出"There are no posts"。这是一个简洁的单行条件判断和输出语句。

![Untitled](assets/php-fundamentals-1/Untitled%2054.png)

- **`$firstPost = !empty($posts[0]) ? $posts[0] : "根本没有帖子";`** 这行代码类似上一行，但它是将结果赋值给变量**`$firstPost`**，而不是直接输出。
- **`$firstPost = !empty($posts[0]) ? $posts[0] : null;`** 这个例子也是使用条件运算符进行赋值，不过这次如果**`$posts[0]`**为空，则赋值为**`null`**。

![Untitled](assets/php-fundamentals-1/Untitled%2055.png)

在PHP中，**`switch`**语句是一种控制结构，用于根据一个变量的值来执行不同的代码分支。它是**`if`**语句的一个替代，特别是在有多个条件需要比较时，**`switch`**语句可以提供更清晰、更易读的代码。

```php
switch (expression) {
  case value1:
    // code to be executed if expression = value1
    break;
  case value2:
    // code to be executed if expression = value2
    break;
  ...
  default:
    // code to be executed if expression is different from all cases
}
```

- **expression**: 这是要评估的表达式，其结果会与各个**`case`**后面的值进行比较。
- **case value**: 如果**`expression`**的结果与**`case`**后面的值匹配，将执行该**`case`**块内的代码。
- **break**: **`break`**语句用于结束**`switch`**块的执行。如果省略，程序将继续执行下一个**`case`**块的代码，这通常不是所期望的行为。
- **default**: **`default`**块是可选的，如果**`expression`**的结果与所有**`case`**都不匹配，将执行**`default`**块的代码。

比如以下例子：

![Untitled](assets/php-fundamentals-1/Untitled%2056.png)

![Untitled](assets/php-fundamentals-1/Untitled%2057.png)

# 循环

PHP中的循环结构允许你重复执行代码块，直到满足指定条件。这在处理数组、生成重复的HTML元素、或执行需要重复任务的时候非常有用。PHP提供了几种类型的循环：

### **1. `for`循环**

**`for`**循环是最常用的循环结构之一，适合于当你提前知道循环次数时使用。

```php
for ($i = 0; $i < 10; $i++) {
    echo $i;
}
```

这个循环会从0开始，增加到9，每次循环增加1。

### **2. `while`循环**

**`while`**循环会在指定的条件为真时重复执行代码块。

```php
$i = 0;
while ($i < 10) {
    echo $i;
    $i++;
}
```

这个循环会执行，直到**`$i`**小于10。

### **3. `do-while`循环**

**`do-while`**循环至少执行一次代码块，然后在指定的条件为真时重复执行。

```php
$i = 0;
do {
    echo $i;
    $i++;
} while ($i < 10);
```

即使条件一开始就是假的，代码块也会执行一次。

### **4. `foreach`循环**

**`foreach`**循环专门用于数组，对数组每个元素执行一次代码块。

```php
$array = [1, 2, 3, 4, 5];
foreach ($array as $value) {
    echo $value;
}
```

这个循环会输出数组**`$array`**中的每个值。

我们来看看下面几个例子：

以下这段PHP代码使用了**`for`**循环来输出从0到10的数字，每个数字后面跟着一个换行标记(**`<br>`**)。

![Untitled](assets/php-fundamentals-1/Untitled%2058.png)

这段代码会在网页上顺序输出以下内容：

![Untitled](assets/php-fundamentals-1/Untitled%2059.png)

以下这段PHP代码使用**`while`**循环来输出数字1到5，每个数字后面跟一个换行(**`<br>`**标签)。

![Untitled](assets/php-fundamentals-1/Untitled%2060.png)

循环会连续输出：

![Untitled](assets/php-fundamentals-1/Untitled%2061.png)

以下这段PHP代码演示了**`do-while`**循环的使用。与**`while`**循环不同，**`do-while`**循环先执行一次循环体内的代码，然后再检查条件是否满足，以决定是否继续执行循环。

![Untitled](assets/php-fundamentals-1/Untitled%2062.png)

结果：

![Untitled](assets/php-fundamentals-1/Untitled%2063.png)

以下这段PHP代码使用**`foreach`**循环遍历数组**`$numbers`**，数组中包含数字1到5。对于数组中的每个元素，循环将其当前值赋给变量**`$x`**，然后执行循环体内的代码。

![Untitled](assets/php-fundamentals-1/Untitled%2064.png)

以下这段PHP代码使用**`foreach`**循环遍历数组**`$posts`**，该数组包含了字符串元素**`'Post One'`**、**`'Post Two'`**、和**`'Post Three'`**。在**`foreach`**循环中，每个元素的索引和值分别被赋予**`$index`**和**`$post`**变量，然后输出这些值。

![Untitled](assets/php-fundamentals-1/Untitled%2065.png)

循环将按照数组中元素的顺序输出每个帖子的索引（从0开始）和值，格式为**`索引 - 值`**：

![Untitled](assets/php-fundamentals-1/Untitled%2066.png)

以下这段代码展示了如何使用**`foreach`**循环遍历关联数组，并且如何在循环中使用数组的键和值。关联数组是由键（key）和值（value）对组成的数组，其中的键是用于标识值的字符串。

![Untitled](assets/php-fundamentals-1/Untitled%2067.png)

循环会按照数组中元素的顺序输出每个键值对，格式为**`键 - 值`**：

![Untitled](assets/php-fundamentals-1/Untitled%2068.png)

# 实战项目：创建联系人簿应用

## 版本1

我们来看看如何管理一个联系人列表，包括初始化联系人数组、添加新联系人、删除联系人，以及通过函数显示所有联系人的详细信息。

### 代码思路

创建**`contact_book.php`文件：**

```php
<?php
// 步骤 1: 初始化联系人数组
...

// 步骤 2: 定义显示所有联系人的函数
...

// 步骤 3: 添加一个新联系人
...

// 步骤 4: 删除一个联系人
...

// 步骤 5: 显示所有联系人
...
?>

```

### **步骤 1: 初始化联系人数组**

```php
$contacts = [
    "John Doe" => ["email" => "john@example.com", "phone" => "123-456-7890"],
    "Jane Doe" => ["email" => "jane@example.com", "phone" => "098-765-4321"]
];
```

- 定义了一个名为**`$contacts`**的关联数组，用来存储联系人的信息。每个联系人的名字作为数组的键，对应的值是另一个关联数组，包含该联系人的电子邮件地址和电话号码。

### **步骤 2: 定义显示所有联系人的函数**

```php
function displayContacts($contacts) {
    foreach ($contacts as $name => $info) {
        echo "Name: $name, Email: ".$info['email'].", Phone: ".$info['phone']."\n";
    }
}
```

- 定义了一个名为**`displayContacts`**的函数，该函数遍历**`$contacts`**数组。对于每个联系人，它使用**`foreach`**循环将联系人的名字、电子邮件和电话号码输出显示。

### **步骤 3: 添加一个新联系人**

```php
$contacts["Alex Smith"] = ["email" => "alex@example.com", "phone" => "555-555-5555"];
```

- 向**`$contacts`**数组中添加一个新的联系人，名为"Alex Smith"。像初始化时一样，新联系人的信息也是通过一个关联数组提供，包括电子邮件和电话号码。

### **步骤 4: 删除一个联系人**

```php
unset($contacts["John Doe"]);
```

- 使用**`unset`**函数从**`$contacts`**数组中删除"John Doe"这个联系人。**`unset`**函数移除指定的键及其对应的值。

### **步骤 5: 显示所有联系人**

```php
displayContacts($contacts);
```

- 调用**`displayContacts`**函数显示更新后的联系人列表。由于之前已经添加了一个新联系人并删除了一个联系人，所以这一步将输出更新后的联系人信息。

### **结果**

执行这段代码后，将输出剩余联系人的名字、电子邮件和电话号码，格式为："Name: 名字, Email: 电子邮件, Phone: 电话号码"。由于"John Doe"已被删除，所以不会显示其信息。新增的"Alex Smith"将会显示在列表中。

## 版本2

在这个版本中，我们使用PHP和HTML创建一个简单的联系人簿应用，包括添加和显示联系人。

### 代码思路

**`contact_book.php`文件：**

```php
<?php
// Step 2: 启动会话
...

// Step 3: 初始化联系人数组
...

// Step 4: 定义显示联系人的函数
...

// Step 5: 处理表单提交
if (...) {
    ...

    // Step 6: 显示所有联系人
    ...
}

?>
<!-- Step 1: HTML表单构建 -->
...
```

### **Step 1: HTML表单构建**

- 首先，使用HTML创建一个表单，用于收集联系人的姓名、电子邮箱和电话号码。这个表单使用**`POST`**方法提交数据到**`contact_book.php`**。
    
    ```php
    <!DOCTYPE html>
    <html lang="zh">
    <head>
        <meta charset="UTF-8">
        <title>联系人簿</title>
    </head>
    <body>
        <h2>添加联系人</h2>
        <form action="contact_book.php" method="post">
            <label for="name">姓名:</label><br>
            <input type="text" id="name" name="name" required><br>
            
            <label for="email">电子邮箱:</label><br>
            <input type="email" id="email" name="email" required><br>
            
            <label for="phone">电话:</label><br>
            <input type="text" id="phone" name="phone" required><br>
            
            <input type="submit" value="添加联系人">
        </form>
    </body>
    </html>
    
    ```
    

### **Step 2: 启动会话**

- 使用**`session_start();`**启动一个新的会话或者恢复现有会话。这是为了在用户的浏览器会话中存储联系人信息。
    
    ```php
    session_start(); // 启动会话
    ```
    

### **Step 3: 初始化联系人数组**

- 判断**`$_SESSION['contacts']`**是否已设置，如果没有，则初始化为一个空数组。这步骤确保了可以安全地向**`$_SESSION['contacts']`**数组中添加新联系人。
    
    ```php
    if (!isset($_SESSION['contacts'])) {
        $_SESSION['contacts'] = [];
    }
    ```
    

### **Step 4: 定义显示联系人的函数**

- 定义了**`displayContacts`**函数，该函数接受一个联系人数组作为参数，遍历该数组，并输出每个联系人的姓名、电子邮箱和电话号码。与之前示例的不同之处在于，此处使用会话（**`$_SESSION`**）来存储和传递联系人数据，而之前的例子是直接操作一个局部变量。
    
    ```php
    function displayContacts($contacts) {
        foreach ($contacts as $contact) {
            echo "Name: ".$contact['name'].", Email: ".$contact['email'].", Phone: ".$contact['phone']."<br>";
        }
    }
    ```
    

### **Step 5: 处理表单提交**

- 检查是否通过**`POST`**方法提交了表单。如果是，从表单中提取出姓名、电子邮箱和电话号码，并将这些数据作为一个关联数组添加到**`$_SESSION['contacts']`**数组中。
    
    ```php
    // 检查是否提交了表单
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $name = $_POST['name'];
        $email = $_POST['email'];
        $phone = $_POST['phone'];
    
        // 将新联系人添加到联系人数组中
        $_SESSION['contacts'][] = ['name' => $name, 'email' => $email, 'phone' => $phone];
    
        // 显示所有联系人
        ...
    }
    ```
    

### **Step 6: 显示所有联系人**

- 调用**`displayContacts`**函数，传入**`$_SESSION['contacts']`**作为参数，以显示当前会话中存储的所有联系人信息。
    
    ```php
    displayContacts($_SESSION['contacts']);
    ```
    

### 重构思路

- **存储机制的变化**：之前的示例直接操作了一个在脚本执行期间定义的变量**`$contacts`**。重构后的代码使用PHP会话（通过**`$_SESSION`**超全局变量）来存储联系人数据，使得数据可以跨多个页面请求保持。
- **数据提交方式的引入**：引入了HTML表单，允许用户输入新的联系人信息，并通过表单提交这些信息，而之前的例子中联系人数据是直接在代码中定义的。

## 版本3

此版本进一步发展了之前的联系人簿应用，增加了删除联系人的功能，并优化了添加联系人的表单处理。

### 代码思路

**`contact_book.php`文件：**

```php
<?php
// Step 1: 启动会话和初始化联系人数组
...

// Step 2: 显示联系人的函数
...

// Step 3: 处理添加联系人的表单
...

// Step 4: 删除联系人的处理
...

// 执行显示联系人函数
displayContacts($_SESSION['contacts']);
?>

<!-- Step 5: HTML表单优化 -->
...

```

### **Step 1: 启动会话和初始化联系人数组**

- 使用**`session_start();`**开始一个新的会话或恢复现有会话。
- 检查**`$_SESSION['contacts']`**是否已经设置。如果没有，就用两个预设的联系人初始化它。这保证了即使在会话的开始阶段也有默认的联系人信息可供显示。
    
    ```php
    // 启动会话以存储联系人信息
    session_start();
    
    // 如果会话中尚未初始化联系人数组，则进行初始化
    if (!isset($_SESSION['contacts'])) {
        $_SESSION['contacts'] = [
            "John Doe" => ["email" => "john@example.com", "phone" => "123-456-7890"],
            "Jane Doe" => ["email" => "jane@example.com", "phone" => "098-765-4321"]
        ];
    }
    ```
    

### **Step 2: 显示联系人的函数**

- **`displayContacts`**函数遍历联系人数组，并为每个联系人生成HTML输出。与之前相比，新增了一个“删除”链接，通过传递联系人姓名作为**`$_GET['delete']`**参数，允许用户请求删除操作。
    
    ```php
    function displayContacts($contacts) {
        foreach ($contacts as $name => $info) {
            echo "<p>姓名: $name, 电子邮件: ".$info['email'].", 电话: ".$info['phone'];
            echo " <a href='?delete=" . urlencode($name) . "'>删除</a></p>";
        }
    }
    ```
    

### **Step 3: 处理添加联系人的表单**

- 检查是否以**`POST`**方法提交了表单，并且检查了表单提交按钮**`addContact`**的存在性，以确保是从添加联系人的表单触发的。
- 从表单获取**`name`**、**`email`**和**`phone`**字段，并在验证它们非空后，将新联系人添加到**`$_SESSION['contacts']`**数组中。
    
    ```php
    if ($_SERVER['REQUEST_METHOD'] == "POST" && isset($_POST['addContact'])) {
        $name = $_POST['name'];
        $email = $_POST['email'];
        $phone = $_POST['phone'];
        if (!empty($name) && !empty($email) && !empty($phone)) {
            $_SESSION['contacts'][$name] = ['email' => $email, 'phone' => $phone];
        }
    }
    ```
    

### **Step 4: 删除联系人的处理**

- 新增了通过**`$_GET['delete']`**参数检查是否有删除请求。如果有，就从**`$_SESSION['contacts']`**数组中删除对应的联系人条目。
    
    ```php
    if (isset($_GET['delete'])) {
        $name = $_GET['delete'];
        unset($_SESSION['contacts'][$name]);
    }
    
    ```
    

### **Step 5: HTML表单优化**

- HTML部分增加了对表单提交按钮**`name="addContact"`**的定义，这用于区分表单提交是用于添加新联系人。
- 与之前代码相比，表单中的**`action`**属性被移除，这意味着表单提交到当前脚本（自引用表单处理）。
    
    ```php
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>联系人簿</title>
    </head>
    <body>
        <h2>添加联系人</h2>
        <form method="POST">
            <label for="name">姓名:</label>
            <input type="text" id="name" name="name" required>
            <label for="email">电子邮件:</label>
            <input type="email" id="email" name="email" required>
            <label for="phone">电话:</label>
            <input type="text" id="phone" name="phone" required>
            <button type="submit" name="addContact">添加联系人</button>
        </form>
    </body>
    </html>
    ```
    

### **从之前的代码到当前代码的重要变化**

- **删除功能的添加**：通过在联系人旁边添加一个“删除”链接，并处理该链接的点击事件来实现删除功能。这增加了用户与联系人簿交互的能力。
- **表单处理的精细化**：引入了**`addContact`**按钮的**`name`**属性，以更准确地检测添加联系人的表单提交，这提高了代码的健壮性和可读性。

## 实验结束

<aside>
💡 提交「实战项目：创建联系人簿应用」的关键结果截图到学习通！！

</aside>