
编程时经常需要检查一系列条件，并据此决定采取什么措施。在Python中，if 语句让你能够检查程序的当前状态，并据此采取相应的措施。

## 5.1　一个简单示例


```python
cars = ['audi', 'bmw', 'subaru', 'toyota']

for car in cars:
    if car == 'bmw':
        print(car.upper())  #对于汽车名'bmw' ，以全大写的方式打印
    else:
        print(car.title())  #其他的汽车以首字母大写的方式打印
```

    Audi
    BMW
    Subaru
    Toyota


## 5.2　条件测试
每条if语句的核心都是一个值为True或False的表达式，这种表达式被称为`条件测试`。

Python根据条件测试的值为True还是False来决定是否执行if语句中的代码。如果条件测试的值为True，Python就执行紧跟在if语句后面的代码；如果为False，Python就忽略这些代码。

### 5.2.1 检查是否相等
首先使用一个等号将car 的值设置为'bmw'。接下来，使用两个等号（==）检查car 的值是否为'bmw'。这个相等运算符在它两边的值相等时返回True ，否则返回False 。两边的值相等，因此Python返回True 。如果变量car的值不是'audi'，测试将返回False。


```python
car = 'bmw'
print(car == 'bmw')
```

    True



```python
print(car == 'audi')
```

    False


### 5.2.2　检查是否相等时不考虑大小写
在Python中检查是否相等时区分大小写，如果大小写很重要，这种行为有其优点；但如果大小写无关紧要，而只想检查变量的值，可将变量的值转换为小写或大写，再进行比较。
> 函数lower() 不会修改存储在变量car 中的值，因此进行这样的比较时不会影响原来的变量。


```python
car = 'Audi'
print(car == 'audi')
print(car.lower() == 'audi'.lower())
print(car.upper() == 'audi'.upper())
```

    False
    True
    True


### 5.2.3　检查是否不相等
要判断两个值是否不等，可结合使用惊叹号和等号（!= ），其中的惊叹号表示不，在很多编程语言中都如此。


```python
requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
    print("Hold the anchovies!")
```

    Hold the anchovies!


### 5.2.4　比较数字
条件语句中可包含各种数学比较，如小于(<)、小于等于(<=)、大于(>)、大于等于(>=)。


```python
age = 18
print(age == 18)
```

    True



```python
answer = 17
if answer != 42:
    print("That is not the correct answer. Please try again!")
```

    That is not the correct answer. Please try again!



```python
age = 21
print(age < 21)
print(age <= 21)
print(age > 21)
print(age >= 21)
```

    False
    True
    False
    True


### 5.2.5　检查多个条件

1. 使用and 检查多个条件

要检查是否两个条件都为True，可使用关键字and将两个条件测试合而为一；如果每个测试都通过了，整个表达式就为True；如果至少有一个测试没有通过，整个表达式就为False。
> 为改善可读性，可将每个测试都分别放在一对括号内，但并非必须这样做。


```python
age_0 = 22
age_1 = 18
print(age_0 >= 21 and age_1 >= 21)
print((age_0 >= 21) & (age_1 >= 21))
age_1 = 22
print(age_0 >= 21 and age_1 >= 21)
print((age_0 >= 21) and (age_1 >= 21))
```

    False
    False
    True
    True


2. 使用or 检查多个条件

关键字or也能够检查多个条件，但只要至少有一个条件满足，就能通过整个测试。仅当两个测试都没有通过时，使用or的表达式才为False 。

> 另注意，类似与C,|和&分别表示or和and。但是尤其要注意运算的优先级。


```python
age_0 = 22
age_1 = 18
print(age_0 >= 21 or age_1 >= 21)
print((age_0 >= 21) | (age_1 >= 21))
print(age_0 >= 21 | age_1 >= 21)
age_0 = 18
print(age_0 >= 21 or age_1 >= 21)
print((age_0 >= 21) | (age_1 >= 21))
```

    True
    True
    False
    False
    False


### 5.2.6　检查特定值是否包含在列表中
要判断特定的值是否已包含在列表中，可使用关键字in。


```python
requested_toppings = ['mushrooms', 'onions', 'pineapple']
print('mushrooms' in requested_toppings)
print('pepperoni' in requested_toppings)
```

    True
    False


### 5.2.7　检查特定值是否不包含在列表中
确定特定的值未包含在列表中很重要；在这种情况下，可使用关键字not in。


```python
banned_users = ['andrew', 'carolina', 'david']
user = 'marie'
if user not in banned_users:
    print(user.title() + ", you can post a response if you wish.")
```

    Marie, you can post a response if you wish.


### 5.2.8　布尔表达式
布尔表达式不过是条件测试的别名。与条件表达式一样，布尔表达式的结果要么为True，要么为False。布尔值通常用于记录条件。


```python
game_active = True
can_edit = False
print(game_active, can_edit)
```

    True False


**练习：**
5-1 条件测试 ：编写一系列条件测试；将每个测试以及你对其结果的预测和实际结果都打印出来。

详细研究实际结果，直到你明白了它为何为True 或False 。

创建至少10个测试，且其中结果分别为True 和False 的测试都至少有5个。

5-2 更多的条件测试 ：你并非只能创建10个测试。如果你想尝试做更多的比较，可再编写一些测试，并将它们加入到conditional_tests.py中。对于下面列出的各种测试，至少编写一个结果为True 和False 的测试。

检查两个字符串相等和不等。

使用函数lower()的测试。

检查两个数字相等、不等、大于、小于、大于等于和小于等于。

使用关键字and 和or 的测试。

测试特定的值是否包含在列表中。

测试特定的值是否未包含在列表中。


```python
# 5-1
print('-----5-1-----')
car = 'subaru'
print("Is car == 'subaru'? I predict True. Actually it's {}".format(car == 'subaru'))
print("Is car == 'audi'? I predict False. Actually it's {}".format(car == 'audi'))
number = 55
print("Is number == 44? I predict True. Actually it's {}".format(number == 44))
print("Is number == 55? I predict False. Actually it's {}".format(number == 55))
# 5-2
print('-----5-2-----')
string_1 = 'string_1'
string_2 = 'String_1'
print(string_1 == string_2, string_1 != string_2)
print(string_1.lower() == string_2.lower(), string_1.lower() != string_2.lower())
number_1 = 55
number_2 = 66
print(number_1 == number_2, number_1 != number_2, number_1 > number_2, number_1 < number_2, \
     number_1 <= number_2, number_1 >= number_2)
print(string_1 == string_2 and number_1 != number_2)
print(string_1 != string_2 or number_1 <= number_2)
numbers = [1,2,3,4,5,6,7,8,10]
print(9 in numbers)
print(8 not in numbers)
```

    -----5-1-----
    Is car == 'subaru'? I predict True. Actually it's True
    Is car == 'audi'? I predict False. Actually it's False
    Is number == 44? I predict True. Actually it's False
    Is number == 55? I predict False. Actually it's True
    -----5-2-----
    False True
    True False
    False True False True True False
    False
    True
    False
    False


## 5.3　if 语句
### 5.3.1　简单的if 语句
最简单的if语句只有一个测试和一个操作。


```python
age = 19
if age >= 18:
    print("You are old enough to vote!")
```

    You are old enough to vote!


在if语句中，缩进的作用与for循环中相同。如果测试通过了，将执行if语句后面所有缩进的代码行，否则将忽略它们。

在紧跟在if语句后面的代码块中，可根据需要包含任意数量的代码行。


```python
age = 19
if age >= 18:
    print("You are old enough to vote!")
    print("Have you registered to vote yet?")
```

    You are old enough to vote!
    Have you registered to vote yet?


### 5.3.2　if-else 语句
经常需要在条件测试通过了时执行一个操作，并在没有通过时执行另一个操作；在这种情况下，可使用Python提供的if-else语句。

if-else语句块类似于简单的if语句，但其中的else 语句让你能够指定条件测试未通过时要执行的操作。

if-else 结构非常适合用于要让Python执行两种操作之一的情形。在这种简单的if-else 结构中，总是会执行两个操作中的一个。


```python
age = 17
if age >= 18:
    print("You are old enough to vote!")
    print("Have you registered to vote yet?")
else:
    print("Sorry, you are too young to vote.")
    print("Please register to vote as soon as you turn 18!")
```

    Sorry, you are too young to vote.
    Please register to vote as soon as you turn 18!


### 5.3.3　if-elif-else 结构
经常需要检查超过两个的情形，为此可使用Python提供的if-elif-else 结构。

Python只执行if-elif-else 结构中的一个代码块，它依次检查每个条件测试，直到遇到通过了的条件测试。测试通过后，Python将执行紧跟在它后面的代码，并跳过余下的测试。


```python
age = 12

if age < 4:
    print("Your admission cost is $0.")
elif age < 18:
    print("Your admission cost is $5.")
else:
    print("Your admission cost is $10.")
```

    Your admission cost is $5.



```python
age = 12

if age < 4:
    price = 0
elif age < 18:
    price = 5
else:
    price = 10

print("Your admission cost is ${}.".format(price))
```

    Your admission cost is $5.


### 5.3.4　使用多个elif 代码块
可根据需要使用任意数量的elif代码块。


```python
age = 66

if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
else:
    price = 3
    
print("Your admission cost is ${}.".format(price))
```

    Your admission cost is $3.


### 5.3.5　省略else 代码块
Python并不要求if-elif结构后面必须有else代码块。在有些情况下，else代码块很有用；而在其他一些情况下，使用一条elif语句来处理特定的情形更清晰。

> else 是一条包罗万象的语句，只要不满足任何if或elif中的条件测试，其中的代码就会执行，这可能会引入无效甚至恶意的数据。如果知道最终要测试的条件，应考虑使用一个elif代码块来代替else代码块。这样就可以肯定，仅当满足相应的条件时，代码才会执行。


```python
age = 12

if age < 4:
    price = 0
elif age < 18:
    price = 5
elif age < 65:
    price = 10
elif age >= 65:
    price = 3
    
print("Your admission cost is ${}.".format(price))
```

    Your admission cost is $5.


### 5.3.6　测试多个条件

if-elif-else 结构功能强大，但仅适合用于只有一个条件满足的情况：遇到通过了的测试后，Python就跳过余下的测试。这种行为很好，效率很高，让你能够测试一个特定的条件。

然而，有时候必须检查你关心的所有条件。在这种情况下，应使用一系列不包含elif和else代码块的简单if语句。在可能有多个条件为True，且你需要在每个条件为True时都采取相应措施时，适合使用这种方法。


```python
requested_toppings = ['mushrooms', 'extra cheese']

if 'mushrooms' in requested_toppings:
    print("Adding mushrooms.")
if 'pepperoni' in requested_toppings:
    print("Adding pepperoni.")
if 'extra cheese' in requested_toppings:
    print("Adding extra cheese.")

print("\nFinished making your pizza!")
```

    Adding mushrooms.
    Adding extra cheese.
    
    Finished making your pizza!



```python
requested_toppings = ['mushrooms', 'extra cheese']

if 'mushrooms' in requested_toppings:
    print("Adding mushrooms.")
elif 'pepperoni' in requested_toppings:
    print("Adding pepperoni.")
elif 'extra cheese' in requested_toppings:
    print("Adding extra cheese.")

print("\nFinished making your pizza!")
```

    Adding mushrooms.
    
    Finished making your pizza!


如果你只想执行一个代码块，就使用if-elif-else 结构；如果要运行多个代码块，就使用一系列独立的if 语句。

**练习：**
5-3 外星人颜色#1 ：假设在游戏中刚射杀了一个外星人，请创建一个名为alien_color 的变量，并将其设置为'green' 、'yellow' 或'red' 。

编写一条if 语句，检查外星人是否是绿色的；如果是，就打印一条消息，指出玩家获得了5个点。

编写这个程序的两个版本，在一个版本中上述测试通过了，而在另一个版本中未通过（未通过测试时没有输出）。

5-4 外星人颜色#2 ：像练习5-3那样设置外星人的颜色，并编写一个if-else 结构。

如果外星人是绿色的，就打印一条消息，指出玩家因射杀该外星人获得了5个点。

如果外星人不是绿色的，就打印一条消息，指出玩家获得了10个点。

编写这个程序的两个版本，在一个版本中执行if 代码块，而在另一个版本中执行else 代码块。

5-5 外星人颜色#3 ：将练习5-4中的if-else 结构改为if-elif-else 结构。

如果外星人是绿色的，就打印一条消息，指出玩家获得了5个点。

如果外星人是黄色的，就打印一条消息，指出玩家获得了10个点。

如果外星人是红色的，就打印一条消息，指出玩家获得了15个点。

编写这个程序的三个版本，它们分别在外星人为绿色、黄色和红色时打印一条消息。

5-6 人生的不同阶段 ：设置变量age 的值，再编写一个if-elif-else 结构，根据age 的值判断处于人生的哪个阶段。

如果一个人的年龄小于2岁，就打印一条消息，指出他是婴儿。

如果一个人的年龄为2（含）～4岁，就打印一条消息，指出他正蹒跚学步。

如果一个人的年龄为4（含）～13岁，就打印一条消息，指出他是儿童。

如果一个人的年龄为13（含）～20岁，就打印一条消息，指出他是青少年。

如果一个人的年龄为20（含）～65岁，就打印一条消息，指出他是成年人。

如果一个人的年龄超过65（含）岁，就打印一条消息，指出他是老年人。

5-7 喜欢的水果 ：创建一个列表，其中包含你喜欢的水果，再编写一系列独立的if 语句，检查列表中是否包含特定的水果。

将该列表命名为favorite_fruits ，并在其中包含三种水果。

编写5条if 语句，每条都检查某种水果是否包含在列表中，如果包含在列表中，就打印一条消息，如“You really like bananas!”。


```python
# 5-3
print("-----5-3-----")
alien_color = 'green'
if alien_color == 'green':
    print("Player gets 5 points.")
alien_color = 'red'
if alien_color == 'green':
    print("Player gets 5 points.")
# 5-4
print("-----5-4-----")
if alien_color == 'green':
    score = 5
else:
    score = 10
print("Player gets {} points.".format(score))
# 5-5
print("-----5-5-----")
if alien_color == "green":
    score = 5
elif alien_color == "yellow":
    score = 10
else:
    score = 15
print("Player gets {} points.".format(score))
# 5-6
print("-----5-6-----")
age = 38
if age < 2:
    status = "infant"
elif age < 4:
    status = "baby"
elif age < 13:
    status = "child"
elif age < 20:
    status = "teenage"
elif age < 65:
    status = "adult"
elif age >= 65:
    status = "aged"
print("{} years old is {}".format(age, status))
# 5-7
print("-----5-7-----")
favorite_fruits = ["bananas", "apples", "cherries", "oranges"]
fruit = "bananas"
if fruit in favorite_fruits:
    print("You really like {}!".format(fruit))
```

    -----5-3-----
    Player gets 5 points.
    -----5-4-----
    Player gets 10 points.
    -----5-5-----
    Player gets 15 points.
    -----5-6-----
    38 years old is adult
    -----5-7-----
    You really like bananas!


## 5.4　使用if 语句处理列表
### 5.4.1　检查特殊元素


```python
requested_toppings = ['mushrooms', 'green peppers', 'extra cheese']

for requested_topping in requested_toppings:
    print("Adding {}.".format(requested_topping))

print("\nFinished making your pizza!")
```

    Adding mushrooms.
    Adding green peppers.
    Adding extra cheese.
    
    Finished making your pizza!



```python
requested_toppings = ['mushrooms', 'green peppers', 'extra cheese']

for requested_topping in requested_toppings:
    if requested_topping == 'green peppers':
        print("Sorry, we are out of green peppers right now.")
    else:
        print("Adding " + requested_topping + ".")

print("\nFinished making your pizza!")
```

    Adding mushrooms.
    Sorry, we are out of green peppers right now.
    Adding extra cheese.
    
    Finished making your pizza!


### 5.4.2 确定列表不是空的
到目前为止，对于处理的每个列表都做了一个简单的假设，即假设它们都至少包含一个元素。我们马上就要让用户来提供存储在列表中的信息，因此不能再假设循环运行时列表不是空的。有鉴于此，在运行for 循环前确定列表是否为空很重要。


```python
requested_toppings = []

if requested_toppings:
    for requested_topping in requested_toppings:
        print("Adding " + requested_topping + ".")
    print("\nFinished making your pizza!")
else:
    print("Are you sure you want a plain pizza?")
```

    Are you sure you want a plain pizza?


首先创建了一个空列表，其中不包含元素。然后进行了简单检查，而不是直接执行for循环。在if语句中将列表名用在条件表达式中时，Python将在列表至少包含一个元素时返回True，并在列表为空时返回False。

### 5.4.3　使用多个列表


```python
available_toppings = ['mushrooms', 'olives', 'green peppers',
                        'pepperoni', 'pineapple', 'extra cheese']

requested_toppings = ['mushrooms', 'french fries', 'extra cheese']

for requested_topping in requested_toppings:
    if requested_topping in available_toppings:
        print("Adding " + requested_topping + ".")
    else:
        print("Sorry, we don't have " + requested_topping + ".")

print("\nFinished making your pizza!")
```

    Adding mushrooms.
    Sorry, we don't have french fries.
    Adding extra cheese.
    
    Finished making your pizza!


**练习：**
5-8 以特殊方式跟管理员打招呼 ：创建一个至少包含5个用户名的列表，且其中一个用户名为'admin' 。想象你要编写代码，在每位用户登录网站后都打印一条问候消息。遍历用户名列表，并向每位用户打印一条问候消息。

如果用户名为'admin' ，就打印一条特殊的问候消息，如“Hello admin, would you like to see a status report?”。

否则，打印一条普通的问候消息，如“Hello Eric, thank you for logging in again”。

5-9 处理没有用户的情形 ：在为完成练习5-8编写的程序中，添加一条if 语句，检查用户名列表是否为空。

如果为空，就打印消息“We need to find some users!”。

删除列表中的所有用户名，确定将打印正确的消息。

5-10 检查用户名 ：按下面的说明编写一个程序，模拟网站确保每位用户的用户名都独一无二的方式。

创建一个至少包含5个用户名的列表，并将其命名为current_users 。

再创建一个包含5个用户名的列表，将其命名为new_users ，并确保其中有一两个用户名也包含在列表current_users 中。

遍历列表new_users ，对于其中的每个用户名，都检查它是否已被使用。如果是这样，就打印一条消息，指出需要输入别的用户名；否则，打印一条消息，指出这个用户名未被使用。

确保比较时不区分大消息；换句话说，如果用户名'John' 已被使用，应拒绝用户名'JOHN' 。

5-11 序数 ：序数表示位置，如1st和2nd。大多数序数都以th结尾，只有1、2和3例外。

在一个列表中存储数字1~9。

遍历这个列表。

在循环中使用一个if-elif-else 结构，以打印每个数字对应的序数。输出内容应为1st 、2nd 、3rd 、4th 、5th 、6th 、7th 、8th 和9th ，但每个序数都独占一行。


```python
# 5-8
print("-----5-8-----")
#users = ['admin', 'mike', 'john', 'alice', 'helen']
users = []
for user in users:
    if user == 'admin':
        print("Hello {}, would you like to see a status report?".format(user))
    else:
        print("Hello {}, thank you for logging in again.".format(user))
# 5-9
print("-----5-9-----")
if users:
    for user in users:
        if user == 'admin':
            print("Hello {}, would you like to see a status report?".format(user))
        else:
            print("Hello {}, thank you for logging in again.".format(user))
else:
    print("We need to find some users!")

# 5-10
print("-----5-10-----")
current_users = ['frank', 'mike', 'john', 'alice', 'helen']
new_users = ['trump', 'Mike', 'Biden', 'ALice', 'Clinton']
for user in new_users:
    if user.lower() in [current_user.lower() for current_user in current_users]:
        print("{} is used.".format(user))
    else:
        print("{} can be used.".format(user))
# 5-11
print("-----5-11-----")
numbers = list(range(1,10))
for number in numbers:
    if number ==  1:
        print("{}st".format(number),end="\t")
    elif number ==  2:
        print("{}nd".format(number),end="\t")
    elif number ==  3:
        print("{}rd".format(number),end="\t")
    else:
        print("{}th".format(number),end="\t")
```

    -----5-8-----
    -----5-9-----
    We need to find some users!
    -----5-10-----
    trump can be used.
    Mike is used.
    Biden can be used.
    ALice is used.
    Clinton can be used.
    -----5-11-----
    1st	2nd	3rd	4th	5th	6th	7th	8th	9th	

5.5　设置if 语句的格式
本章的每个示例都展示了良好的格式设置习惯。在条件测试的格式设置方面，PEP 8提供的唯一建议是，在诸如== 、>= 和<= 等比较运算符两边各添加一个空格，例如，`if age < 4:` 要比`if age<4:` 好。

这样的空格不会影响Python对代码的解读，而只是让代码阅读起来更容易。

**练习：**

5-12 设置if 语句的格式 ：审核你在本章编写的程序，确保正确地设置了条件测试的格式。

5-13 自己的想法 ：与刚拿起本书时相比，现在你是一名能力更强的程序员了。鉴于你对如何在程序中模拟现实情形有了更深入的认识，你可以考虑使用程序来解决一些问题。随着编程技能不断提高，你可能想解决一些问题，请将这方面的想法记录下来。想想你可能想编写的游戏、想研究的数据集以及想创建的Web应用程序。

----
![欢迎关注我的微信公众号](https://blog.flashield.com/images/WeChat_QRCode_200.png)
欢迎关注我的微信公众号一起交流！