# 第七章、用户输入和while循环


在本章中，将学习如何接受用户输入，让程序能够对其进行处理。为此，你需要使用函数input()。

还将学习如何让程序不断地运行，让用户能够根据需要输入信息，并在程序中使用这些信息。为此，需要使用while循环让程序不断地运行，直到指定的条件不满足为止。

通过获取用户输入并学会控制程序的运行时间，可编写出交互式程序。

## 7.1　函数input() 的工作原理
函数input()让程序暂停运行，等待用户输入一些文本。获取用户输入后，Python将其存储在一个变量中，以方便后续使用。

函数input() 接受一个参数：即要向用户显示的提示 或说明，让用户知道该如何做。

> 注意：如果使用Sublime Text，是不能运行提示用户输入的程序。你可以使用Sublime Text来编写提示用户输入的程序，但必须从终端运行它们。


```python
message = input("Tell me something, and I will repeat it back to you: ")
print(message)
```

    Tell me something, and I will repeat it back to you: Hello
    Hello


### 7.1.1　编写清晰的程序
每当使用函数input()时，都应指定清晰而易于明白的提示，准确地指出希望用户提供什么样的信息。

通过在提示末尾（这里是冒号后面）包含一个空格，可将提示与用户输入分开，让用户清楚地知道其输入始于何处


```python
name = input("Please enter your name: ")
print("Hello, " + name.title() + "!")
```

    Please enter your name: Bin
    Hello, Bin!


有时候，提示可能超过一行，例如，你可能需要指出获取特定输入的原因。在这种情况下，可将提示存储在一个变量中，再将该变量传递给函数input()。这样，即便提示超过一行，input()语句也非常清晰。


```python
prompt = "If you tell us who you are, we can personalize the messages you see."
prompt += "\nWhat is your first name? "

name = input(prompt)
print("\nHello, " + name.title() + "!")
```

    If you tell us who you are, we can personalize the messages you see.
    What is your first name? Bin
    
    Hello, Bin!


### 7.1.2　使用int()来获取数值输入
使用函数input() 时，Python将用户输入解读为字符串。


```python
age = input("How old are you? ")
print(type(age))
try:
    print(age >= 18)
except Exception as e:
    print(e)
```

    How old are you? 38
    <class 'str'>
    '>=' not supported between instances of 'str' and 'int'


为解决这个问题，可使用函数int() ，它让Python将输入视为数值。函数int() 将数字的字符串表示转换为数值表示。


```python
# int()用于整数
age = input("How old are you? ")
age = int(age)
print(age >= 18)
```

    How old are you? 38
    True



```python
height = input("How tall are you, in inches? ")
height = float(height)

if height >= 36:
    print("\nYou're tall enough to ride!")
else:
    print("\nYou'll be able to ride when you're a little older.")
```

    How tall are you, in inches? 35
    
    You'll be able to ride when you're a little older.


将数值输入用于计算和比较前，务必将其转换为数值表示。

### 7.1.3　求模运算符
处理数值信息时，`求模运算符`（%）是一个很有用的工具，它将两个数相除并返回余数。

求模运算符不会指出一个数是另一个数的多少倍，而只指出余数是多少。

如果一个数可被另一个数整除，余数就为0，因此求模运算符将返回0。


```python
print(4 % 3)
print(5 % 3)
print(6 % 3)
print(7 % 3)
```

    1
    2
    0
    1



```python
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)

if number % 2 == 0:
    print("The number {} is even.".format(number))
else:
    print("The number {} is odd.".format(number))
```

    Enter a number, and I'll tell you if it's even or odd: 38
    The number 38 is even.


### 7.1.4　在Python 2.7中获取输入
如果你使用的是Python 2.7，应使用函数raw_input()来提示用户输入。这个函数与Python 3中的input()一样，也将输入解读为字符串。

> Python 2.7也包含函数input() ，但它将用户输入解读为Python代码，并尝试运行它们。因此，最好的结果是出现错误，指出Python不明白输入的代码；而最糟的结果是，将运行你原本无意运行的代码。如果你使用的是Python 2.7，请使用raw_input()而不是input()来获取输入。

**练习：**
7-1 汽车租赁 ：编写一个程序，询问用户要租赁什么样的汽车，并打印一条消息，如“Let me see if I can find you a Subaru”。

7-2 餐馆订位 ：编写一个程序，询问用户有多少人用餐。如果超过8人，就打印一条消息，指出没有空桌；否则指出有空桌。

7-3 10的整数倍 ：让用户输入一个数字，并指出这个数字是否是10的整数倍。


```python
# 7-1
print("-----7-1-----")
car = input("Which brand of car do you want? ")
print("Let me see if I can find you a {}".format(car.title()))
# 7-2
print("-----7-2-----")
people_number = int(input("How many people?"))
if people_number > 8:
    print("No more desk.")
else:
    print("Have a desk.")
# 7-3
print("-----7-3-----")
number = int(input("Please Input a Number:"))
if number % 10 == 0:
    print("{} can be divided by 10.".format(number))
else:
    print("{} can't be divided by 10.".format(number))
```

    -----7-1-----
    Which brand of car do you want? audi
    Let me see if I can find you a Audi
    -----7-2-----
    How many people?12
    No more desk.
    -----7-3-----
    Please Input a Number:340
    340 can be divided by 10.


## 7.2　while 循环简介
for循环用于针对集合中的每个元素都一个代码块，而while循环不断地运行，直到指定的条件不满足为止。

### 7.2.1　使用while 循环
你可以使用while 循环来数数。


```python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
```

    1
    2
    3
    4
    5


### 7.2.2　让用户选择何时退出
可使用while 循环让程序在用户愿意时不断地运行。


```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = input(prompt)
while message != 'quit':
    message = input(prompt)
    print(message)
```

    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. Hi
    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. Hello
    Hello
    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. quit
    quit



```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = ""
while message != 'quit':
    message = input(prompt)
    #这里类似于do-while结构
    if message != 'quit':
        print(message)
```

    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. Hello
    Hello
    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. quit


### 7.2.3　使用标志
在要求很多条件都满足才继续运行的程序中，可定义一个变量，用于判断整个程序是否处于活动状态。这个变量被称为`标志`，充当了程序的交通信号灯。

可让程序在标志为True时继续运行，并在任何事件导致标志的值为False时让程序停止运行。这样，在while语句中就只需检查一个条件——标志的当前值是否为True ，并将所有测试（是否发生了应将标志设置为False的事件）都放在其他地方，从而让程序变得更为整洁。


```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "

active = True
while active:
    message = input(prompt)
    if message == 'quit':
        active = False
    else:
        print(message)
```

    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. Hello
    Hello
    
    Tell me something, and I will repeat it back to you:
    Enter 'quit' to end the program. quit


### 7.2.4　使用break 退出循环
要立即退出while 循环，不再运行循环中余下的代码，也不管条件测试的结果如何，可使用break 语句。break 语句用于控制程序流程，可使用它来控制哪些代码行将执行，哪些代码行不执行，从而让程序按你的要求执行你要执行的代码。

> 在任何Python循环中都可使用break 语句。例如，可使用break 语句来退出遍历列表或字典的for 循环。


```python
prompt = "\nPlease enter the name of a city you have visited:"
prompt += "\n(Enter 'quit' when you are finished.) "

while True:
    city = input(prompt)

    if city == 'quit':
        break
    else:
        print("I'd love to go to " + city.title() + "!")
```

    
    Please enter the name of a city you have visited:
    (Enter 'quit' when you are finished.) Nantong
    I'd love to go to Nantong!
    
    Please enter the name of a city you have visited:
    (Enter 'quit' when you are finished.) quit


### 7.2.5　在循环中使用continue
要返回到循环开头，并根据条件测试结果决定是否继续执行循环，可使用continue语句，它不像break语句那样不再执行余下的代码并退出整个循环。


```python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue
    print(current_number)
```

    1
    3
    5
    7
    9


### 7.2.6　避免无限循环
每个while 循环都必须有停止运行的途径，这样才不会没完没了地执行下去。

每个人都会偶尔因不小心而编写出无限循环，在循环的退出条件比较微妙时尤其如此。如果程序陷入无限循环，可按`Ctrl + C`，也可关闭显示程序输出的终端窗口。

要避免编写无限循环，务必对每个while 循环进行测试，确保它按预期那样结束。如果你希望程序在用户输入特定值时结束，可运行程序并输入这样的值；如果在这种情况下程序没有结束，请检查程序处理这个值的方式，确认程序至少有一个这样的地方能让循环条件为False或让break语句得以执行。


```python
x = 1
while x <= 5:
    print(x)
    x += 1
```

    1
    2
    3
    4
    5



```python
# 这个循环将没完没了地运行！
x = 1
while x <= 5:
    #为了手速能跟上
    if x % 100000 == 0:
        print(x)
    x -= 1
```

    0
    -100000
    -200000
    -300000
    -400000
    -500000
    -600000
    -700000
    -800000
    -900000
    -1000000
    -1100000
    -1200000
    -1300000
    -1400000
    -1500000



    ---------------------------------------------------------------------------

    KeyboardInterrupt                         Traceback (most recent call last)

    <ipython-input-18-9158b7c31928> in <module>()
          3 while x <= 5:
          4     #为了手速能跟上
    ----> 5     if x % 100000 == 0:
          6         print(x)
          7     x -= 1


    KeyboardInterrupt: 


**练习：**
7-4 比萨配料 ：编写一个循环，提示用户输入一系列的比萨配料，并在用户输入'quit' 时结束循环。每当用户输入一种配料后，都打印一条消息，说我们会在比萨中添加这种配料。

7-5 电影票 ：有家电影院根据观众的年龄收取不同的票价：不到3岁的观众免费；3~12岁的观众为10美元；超过12岁的观众为15美元。请编写一个循环，在其中询问用户的年龄，并指出其票价。

7-6 三个出口 ：以另一种方式完成练习7-4或练习7-5，在程序中采取如下所有做法。

在while 循环中使用条件测试来结束循环。

使用变量active 来控制循环结束的时机。

使用break 语句在用户输入'quit' 时退出循环。

7-7 无限循环 ：编写一个没完没了的循环，并运行它（要结束该循环，可按Ctrl +C，也可关闭显示输出的窗口）。


```python
# 7-4
#调整一下print和input的顺序就可以很好的处理重复打印quit的问题
print("-----7-4-----")
prompt = "Please Input the toppings:\n Enter quit to exit."
topping=input(prompt)
while topping != "quit":
    print("We will add {} on the pizza.".format(topping))
    topping = input(prompt)
# 7-5
print("-----7-5-----")
prompt = "\nHow old are you?\n Press Enter to quit."
age = input(prompt)
price = 0
while age != "":
    try:
        age = int(age)
        if age <= 0:
            print("Not Born? Please do not kid me!")
            price = "NULL"
        elif age <= 3:
            price = 0
        elif age <= 12:
            price = 12
        else:
            price = 15
        print("The Ticket Price is ${}.".format(price))
        age = input(prompt)
    except Exception as e:
        print("Error:{}".format(e))
        print("Please Enter Correct AGE!")
        age = input(prompt)

# 7-6
print("-----7-6-----")
prompt = "\nHow old are you?\n Press Enter to quit."
age = input(prompt)
active = True
price = 0
while active:
    try:
        age = int(age)
        if age <= 0:
            print("Not Born? Please do not kid me!")
            price = "NULL"
        elif age <= 3:
            price = 0
        elif age <= 12:
            price = 12
        else:
            price = 15
        print("The Ticket Price is ${}.".format(price))
        age = input(prompt)
    except Exception as e:
        print("Error:{}".format(e))
        print("Please Enter Correct AGE!")
        active = False
# 7-7
print("-----7-7-----")
```

    -----7-4-----
    Please Input the toppings:
     Enter quit to exit.mushroom
    We will add mushroom on the pizza.
    Please Input the toppings:
     Enter quit to exit.quit
    -----7-5-----
    
    How old are you?
     Press Enter to quit.4
    The Ticket Price is $12.
    
    How old are you?
     Press Enter to quit.-12
    Not Born? Please do not kid me!
    The Ticket Price is $NULL.
    
    How old are you?
     Press Enter to quit.Hello
    Error:invalid literal for int() with base 10: 'Hello'
    Please Enter Correct AGE!
    
    How old are you?
     Press Enter to quit.4
    The Ticket Price is $12.
    
    How old are you?
     Press Enter to quit.
    -----7-6-----
    
    How old are you?
     Press Enter to quit.Hello
    Error:invalid literal for int() with base 10: 'Hello'
    Please Enter Correct AGE!
    -----7-7-----


## 7.3　使用while 循环来处理列表和字典
到目前为止，我们每次都只处理了一项用户信息：获取用户的输入，再将输入打印出来或作出应答；循环再次运行时，我们获悉另一个输入值并作出响应。然而，要记录大量的用户和信息，需要在while循环中使用列表和字典。

for循环是一种遍历列表的有效方式，但在for循环中不应修改列表，否则将导致Python难以跟踪其中的元素。

要在遍历列表的同时对其进行修改，可使用while循环。通过将while循环同列表和字典结合起来使用，可收集、存储并组织大量输入，供以后查看和显示。

### 7.3.1　在列表之间移动元素


```python
# 首先，创建一个待验证用户列表
# 和一个用于存储已验证用户的空列表
unconfirmed_users = ['alice', 'brian', 'candace']
confirmed_users = []

# 验证每个用户，直到没有未验证用户为止
# 将每个经过验证的列表都移到已验证用户列表中
while unconfirmed_users:
    current_user = unconfirmed_users.pop()

    print("Verifying user: " + current_user.title())
    confirmed_users.append(current_user)

# 显示所有已验证的用户
print("\nThe following users have been confirmed:")
for confirmed_user in confirmed_users:
    print(confirmed_user.title())
```

    Verifying user: Candace
    Verifying user: Brian
    Verifying user: Alice
    
    The following users have been confirmed:
    Candace
    Brian
    Alice


### 7.3.2　删除包含特定值的所有列表元素
我们使用函数remove()来删除列表中的特定值，这之所以可行，是因为要删除的值在列表中只出现了一次。如果要删除列表中**所有**包含特定值的元素，可使用循环。


```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
#print(pets)

while 'cat' in pets:
    pets.remove('cat')

print(pets)
```

    ['dog', 'dog', 'goldfish', 'rabbit']



```python
pets = ['dog', 'cat', 'dog', 'goldfish', 'cat', 'rabbit', 'cat']
#这个效率为什么没有上面的高呢？
for count in range(pets.count('cat')):
    pets.remove('cat')
print(pets)
```

    ['dog', 'dog', 'goldfish', 'rabbit']


### 7.3.3　使用用户输入来填充字典
可使用while循环提示用户输入任意数量的信息。


```python
responses = {}

# 设置一个标志，指出调查是否继续
polling_active = True

while polling_active:
    # 提示输入被调查者的名字和回答
    name = input("\nWhat is your name? ")
    response = input("Which mountain would you like to climb someday? ")
    
    # 将答卷存储在字典中
    responses[name] = response
    
    # 看看是否还有人要参与调查
    repeat = input("Would you like to let another person respond? (yes/ no) ")
    
    if repeat == 'no':
        polling_active = False

# 调查结束，显示结果
print("\n--- Poll Results ---")
for name, response in responses.items():
    print(name + " would like to climb " + response + ".")
```

    
    What is your name? Bin
    Which mountain would you like to climb someday? Himalaya
    Would you like to let another person respond? (yes/ no) yes
    
    What is your name? Judy
    Which mountain would you like to climb someday? LangShan
    Would you like to let another person respond? (yes/ no) no
    
    --- Poll Results ---
    Bin would like to climb Himalaya.
    Judy would like to climb LangShan.


**练习：**
7-8 熟食店 ：创建一个名为sandwich_orders 的列表，在其中包含各种三明治的名字；再创建一个名为finished_sandwiches 的空列表。遍历列表sandwich_orders ，对于其中的每种三明治，都打印一条消息，如I made your tuna sandwich ，并将其移到列表finished_sandwiches 。所有三明治都制作好后，打印一条消息，将这些三明治列出来。

7-9 五香烟熏牛肉（pastrami）卖完了 ：使用为完成练习7-8而创建的列表sandwich_orders ，并确保'pastrami' 在其中至少出现了三次。在程序开头附近添加这样的代码：打印一条消息，指出熟食店的五香烟熏牛肉卖完了；再使用一个while 循环将列表sandwich_orders 中的'pastrami' 都删除。确认最终的列表finished_sandwiches 中不包含'pastrami' 。

7-10 梦想的度假胜地 ：编写一个程序，调查用户梦想的度假胜地。使用类似于“If you could visit one place in the world, where would you go?”的提示，并编写一个打印调查结果的代码块。


```python
# 7-8
print("-----7-8-----")
sandwich_orders = ['tuna','pastrami','egg','pastrami','tomato','tuna','pastrami']
finished_sandwiches = []
while sandwich_orders:
    finished_sandwich = sandwich_orders.pop()
    print("I made your {} sandwich.".format(finished_sandwich))
    finished_sandwiches.append(finished_sandwich)
print("Finished Sandwiches: {}.".format(",".join(finished_sandwiches)))
# 7-9
print("-----7-9-----")
sandwich_orders = ['tuna','pastrami','egg','pastrami','tomato','tuna','pastrami']
print("Pastrami pizzas are sold out.")
soldout_pizza = "pastrami"
while soldout_pizza in sandwich_orders:
    sandwich_orders.remove(soldout_pizza)
print("Ordered Sandwiches: {}.".format(",".join(sandwich_orders)))
# 7-10
print("-----7-10-----")
favorate_places = {}
active = "yes"
while active == "yes":
    name = input("Please Input your name:")
    place = input("Please Input your favorate place:")
    favorate_places[name] = place
    active = input("Investage another person?(yes/no)")
print()
for name, favorate_place in favorate_places.items():
    print("{}'s favorate place is {}.".format(name,favorate_place))
print(favorate_places)
```

    -----7-8-----
    I made your pastrami sandwich.
    I made your tuna sandwich.
    I made your tomato sandwich.
    I made your pastrami sandwich.
    I made your egg sandwich.
    I made your pastrami sandwich.
    I made your tuna sandwich.
    Finished Sandwiches: pastrami,tuna,tomato,pastrami,egg,pastrami,tuna.
    -----7-9-----
    Pastrami pizzas are sold out.
    Ordered Sandwiches: tuna,egg,tomato,tuna.
    -----7-10-----
    Please Input your name:Bin
    Please Input your favorate place:Home
    Investage another person?(yes/no)yes
    Please Input your name:Judy
    Please Input your favorate place:School
    Investage another person?(yes/no)yes
    Please Input your name:Crystal
    Please Input your favorate place:Kindergarten
    Investage another person?(yes/no)no
    
    Bin's favorate place is Home.
    Judy's favorate place is School.
    Crystal's favorate place is Kindergarten.
    {'Bin': 'Home', 'Judy': 'School', 'Crystal': 'Kindergarten'}


----
![欢迎关注我的微信公众号](https://blog.flashield.com/images/WeChat_QRCode_200.png)
欢迎关注我的微信公众号一起交流！