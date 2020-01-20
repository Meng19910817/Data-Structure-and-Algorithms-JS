Recently I learned Data Structure and Algorithms with CoderWhy on Bilibili and his blogs, so I decided to make some notes for the people who did the same thing with me. However, I want to keep practicing English. Then, I made the decision to write coding notes with English. I know that is wired in this community, but I really want to do something with coding and the language I am learning. SO, let's get started!

# Personal Introduction:
​    Hi, Friends. If you are new here, my name is Dejun Zhang, I have been working as a Java Developer for almost 3 years. 

​    A year ago, I quited the office and started to think about my life. During the years, my job responsibility was to code business logic in the traditional coding industry. 

​    NOW, I am trying to improve both my programming skills and English.

​    I know you have read lots of articles of Data Structure and Algorithms in Chinese, now, you have the differrent one! 

​    If I had anything wrong with coding, interpretation and English, please tell me or comment under the blow, let me know. If you like this article, please give me a "thumb up" and subscribe to  me!

## WHY I coded Data Structure with JavaScript NOT Java?

​    The simple answer was I learned this course with JS, Firstly, I want to make notes with JavaScript and get fully understanding of Data Structure with JS. Then I will implement with Java or Python again.

## Have you ever learned Data Structure when you were a Java Developer?

​    I think I get to know some data structures. BUT, I feel like my basic programming skills are weak. SO, I want to study from the beginning. It will be never late if you really want to achieve something.



# Stack

## First In Last Out(FILO)

<img src="/Users/zoumengyu/Library/Application Support/typora-user-images/image-20200119202049213.png" alt="image-20200119202049213" style="zoom:50%;" />

<img src="/Users/zoumengyu/Library/Application Support/typora-user-images/image-20200119202122048.png" alt="image-20200119202122048" style="zoom:50%;" />

We can implement Stack with data structure, Array. Here it is:



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <script>
        //1. creating a class called Stack
        function Stack(){
            this.items = []
            
            //2. Adding oprating methods in it
            //push-Pushing an element in the array
            Stack.prototype.push = function(element){
                this.items.push(element);
            }
            //pop-Poping an element from array
            Stack.prototype.pop = function(){
                return this.items.pop();
            }
            //Peek-Return the toppest element the aarray
            Stack.prototype.peek = function(){
                return this.items[this.items.length -1]
            }
            //size-Return size of array
            Stack.prototype.size = function(){
                return this.items.length
            }
            //isEmpty-If it's empty return true, otherwise false
            Stack.prototype.isEmpty = function(){
                return this.items.length == 0
            }
            //toStr-Return String of the arary
            Stack.prototype.toStr = function(){
                var resultStr =  ''
                for(var i = 0; i < items.length; i++){
                    resultStr += this.items[i] + ""
                }
                return resultStr
            }
        }
		//Testing
    var stack = new Stack();
    stack.push("a")
    stack.push("b")
    stack.push("c")
    console.log(stack)

    console.log(stack.pop())
    console.log(stack.peek())
    console.log(stack.size())
    console.log(stack.isEmpty())
        
    </script>
</body>
</html>
```



