Today, I am going to write about another data structure implemented by the array. It is Queue.

## Queue

### First In First Out(FIFO)

It can be divided into two kinds of queue.

![Queue](../master/images/Queue.png)

1. normal queue.

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
       //1. creating a class called Queue
        function Queue(){
            //Initing the array
           this.items = []
           //the method for putting element into Queue
           Queue.prototype.enQueue = function(element){
               this.items.push(element)
           }
           //the method for delete the first put element, this is different from Stack
           Queue.prototype.deQueue = function(){
               this.items.shift()
           }
           //Return the first element of array
           Queue.prototype.front = function(){
               return this.items[0]
           }
           //Juding array is empty or not
           Queue.prototype.isEmpty = function(){
               return this.items.length == 0
           }
           //Return the numbers of elements
           Queue.prototype.size = function(){
               return this.items.length
           }
        }
   
       //2. Testing
       var queue = new Queue()
       queue.enQueue("Amy") 
       queue.enQueue("Bob") 
       queue.enQueue("Chris")
       console.log(queue)
   
       queue.deQueue()
       console.log(queue)
   
       
       console.log(queue.front())
       console.log(queue.isEmpty())
       console.log(queue.size())
   
   
       </script>
   </body>
   </html>
   ```

   2. Priority queue

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
           //1. Creating a class called PriorityQueue
           function PriorityQueue(){
               this.items = []
               //2. Creating an inner class called Queue
               function Queue(data, priority){
                   this.data = data
                   this.priority = priority
               }
               //3. the method for putting element by priority
               PriorityQueue.prototype.enQueue = function(data, priority){
                   //3.1 Creating instance of Queue, and finishing evaluation
                   var priorityQueue = new Queue(data, priority);
               
                   //3.2 Telling the priority of element and entering it
                   //3.2.1 if it's empty, entering element in it directly
                   if (this.isEmpty()){
                       this.items.push(priorityQueue)
                   } else {
                       //3.2.2 if it's not empty, comparing new element's priority with each element in this array
                       var added = false
                       for(var i = 0; i < this.items.length; i++){
                           if(priorityQueue.priority < this.items[i].priority){
                               this.items.splice(i, 0, priorityQueue)
                               added = true
                               break
                           } 
                       }
                       if (!added){
                           this.items.push(priorityQueue)
                       }
                       
                   }
               } 
               //the method for delete the first put element, this is different from Stack
               PriorityQueue.prototype.deQueue = function(){
                   this.items.shift()
               }
               //Returning the first element of array
               PriorityQueue.prototype.front = function(){
                   return this.items[0]
               }
               //telling the array is empty or not
               PriorityQueue.prototype.isEmpty = function(){
                   return this.items.length == 0
               }
               //Returning the numbers of elements
               PriorityQueue.prototype.size = function(){
                   return this.items.length
               }
           }
   
           //Testing
           var pq = new PriorityQueue()
           pq.enQueue("Amy", 100)
           pq.enQueue("Chris", 97)
           pq.enQueue("Bob", 99)
           pq.enQueue("Echo", 1000)
           pq.enQueue("David", 98)
           
           
           console.log(pq)
   
           pq.deQueue()
           console.log(pq)
   
           console.log(pq.front())
           console.log(pq.size())
           console.log(pq.isEmpty())
       </script>
   </body>
   </html>
   ```

   
