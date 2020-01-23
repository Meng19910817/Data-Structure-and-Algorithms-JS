Array

1. Consecutive space

2. It's more complex to **insert** or **delete** elements in a Array,  we need to change each element' index after inserting an element in the special position(not at the beginning or ending).

   ![Array](../master/images/Array.png)



Node

1. **Non**-consecutive space

2. It's more complex to **read** elements from a ListNode due to the structure, we need to read from the head, each element connected with **next**.

   ![LinkedNode](../master/images/linkedNode.png)

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
           function LinkedNode(){
               this.head = null
               this.length = 0
               function Node(data){
                   this.data = data
                   this.next = null
               }
   
               LinkedNode.prototype.append = function(data){
                   var newNode = new Node(data)
                   //Telling if it's the first node after the head
                   if (this.length == 0){
                       this.head = newNode
                   } else {
                       var current = this.head
                       while(current.next){
                           current = current.next
                       }
                       current.next = newNode 
                   }
                   this.length += 1
               }
   
               LinkedNode.prototype.toStr = function(){
                  var current = this.head
                  var nodeStr = ""
                  
                  while(current){
                       nodeStr += current.data + " "
                       current = current.next
                  } 
                  return nodeStr
               }
   
               LinkedNode.prototype.insert = function(position, data){
                   //1. Telling position is not out of index
                   if (position < 0 || position > this.length)
                       return false
                   var newNode = new Node(data)
                   //2. Telling the position
                   if (position == 0){
                       newNode.next = this.head
                       this.head = newNode
                   } else {
                       var index = 0
                       var current = this.head
                       var previous = null
                       while (index++ < position){
                           previous = current
                           current = current.next
                       }
                       newNode.next = current
                       previous.next = newNode
                   }
                   this.length += 1
                   return true
               }
   
               LinkedNode.prototype.get = function(position){
                   //1.Telling if it's out of index
                   if (position < 0 || position >= this.length)
                       return false
                   var index  = 0;
                   var current = this.head
                   while(index++ < position){
                       current = current.next
                   }
                   return current.data
               }
   
               LinkedNode.prototype.indexOf = function(data){
                   var index  = 0;
                   var current = this.head
                   while(current){
                       if (data == current.data){
                           return index
                       }
                       index += 1
                       current = current.next
                   }
                   return -1
               }
   
               LinkedNode.prototype.update = function(position, data){
                   if (position < 0 || position >= this.length)
                       return false
                   var index = 0
                   var current = this.head
                   while(index++ < position){
                       current = current.next
                   }
                   current.data = data
                   return true
               }
   
               LinkedNode.prototype.removeAt = function(position){
                   if (position < 0 || position >= this.length)
                       return null
                   
                   var current = this.head
                   if(position == 0){
                       this.head = this.head.next
                   } else {
                       var index = 0 
                       var previous = null
                       while(index++ < position){
                           previous = current
                           current = current.next
                       }
                       previous.next = current.next
                   }
   
                   this.length -= 1
                   return current.data
               }
   
               LinkedNode.prototype.remove = function(data){
                   var position = this.indexOf(data)
                   return this.removeAt(position)
               }
   
               LinkedNode.prototype.isEmpty = function(){
                   return this.length == 0
               }
   
               LinkedNode.prototype.size = function(){
                   return this.length
               }
           }
           
           var linkedNode = new LinkedNode();
           linkedNode.append("a")
           linkedNode.append("b")
           linkedNode.append("c")
           console.log(linkedNode.toStr())
   
           linkedNode.insert(0, 111)
           linkedNode.insert(3, 222)
           linkedNode.insert(5, 333)
           // console.log(linkedNode.toStr())
   
           // console.log(linkedNode.get(0))
           // console.log(linkedNode.get(3))
           // console.log(linkedNode.get(5))
   
           // console.log(linkedNode.indexOf(111))
           // console.log(linkedNode.indexOf(222))
           // console.log(linkedNode.indexOf(333))
           // console.log(linkedNode.indexOf(555))
   
           // console.log("======Update data with position======")
           // linkedNode.update(0, 666)
           // console.log(linkedNode.toStr())
   
           console.log("======Testing removeAt() method======")
           linkedNode.removeAt(0)
           console.log(linkedNode.toStr())
   
           console.log("======Testing remove() method======")
           linkedNode.remove(222)
           linkedNode.remove(333)
           console.log(linkedNode.toStr())
       </script>
   </body>
   </html>
   ```

   
