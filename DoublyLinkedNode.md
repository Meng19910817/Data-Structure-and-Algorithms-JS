Today, I'm going to write about another structure based on linkedNode. DoublyLinkedNode is based on LinkedNode, adding tail into it.  The elements in this structure also have addtional previous pointer pointing at the previous element.

![DoublyLinkedNode](../master/images/DoublyLinkedNode.png)

Here is another picture for the method of insert:

![DoublyLinkedNode](../master/images/DoublyLinkedNode_insert.png)



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
        function DoublyLinkedNode(){
            this.head = null
            this.tail = null
            this.length = 0
            function Node(data){
                this.prev = null
                this.data = data
                this.next = null
            }

            DoublyLinkedNode.prototype.append = function(data){
                var newNode = new Node(data)
                if(this.length == 0){
                    this.head = newNode
                    this.tail = newNode
                } else {
                    newNode.prev = this.tail
                    this.tail.next = newNode
                    this.tail = newNode
                }
                this.length += 1
            }
            DoublyLinkedNode.prototype.backwardToStr = function(){
                var current = this.head
                var resultStr =  ""
                while(current){
                    resultStr += current.data + " "
                    current = current.next
                }
                return resultStr
            }
            DoublyLinkedNode.prototype.forwardToStr = function(){
                var current = this.tail
                var resultStr =  ""
                while(current){
                    resultStr += current.data + " "
                    current = current.prev
                }
                return resultStr
            }
            DoublyLinkedNode.prototype.toStr = function(){
                return this.backwardToStr()
            }

            DoublyLinkedNode.prototype.insert = function(position, data){
                if (position < 0 || position > this.length)
                    return false

                var newNode = new Node(data)
                if (this.length == 0){
                    this.head = newNode
                    this.tail = newNode
                } else {
                    if (position == 0){
                        this.head.prev = newNode
                        newNode.next = this.head
                        this.head = newNode
                    } else if (position == this.length){
                        newNode.prev = this.tail
                        this.tail.next = newNode
                        this.tail = newNode
                    } else {
                        var current = this.head
                        var index = 0
                        while (index++ < position){
                            current = current.next
                        }
                        newNode.prev = current.prev
                        current.prev.next = newNode 
                        newNode.next = current                      
                        current.prev = newNode
                    }
                } 
                this.length += 1
                return true
                
            }

            DoublyLinkedNode.prototype.get = function(position){
                if(position < 0 || position >= this.length)
                    return null
                var current = this.head
                var index = 0
                while (index++ < position){
                    current = current.next
                }
                return current.data
            }

            DoublyLinkedNode.prototype.indexOf = function(data){
                var current = this.head
                var index = 0
                while(current){
                    if (current.data == data){
                        return index
                    }
                    current = current.next
                    index++
                }
                return -1
            }
            DoublyLinkedNode.prototype.update = function(position, data){
                if (position < 0 || position >= this.length)
                    return false
                var current = this.head
                var index = 0
                while(index++ < position){
                    current = current.next
                }
                current.data = data
                return true
            }

            DoublyLinkedNode.prototype.removeAt = function(position){
                if (position < 0 || position >= this.length)
                    return null

                var current = this.head
                if (this.length == 1){
                    this.head = null
                    this.tail = null
                } else {
                    if (position == 0){
                        this.head.next.prev = null
                        this.head = this.head.next
                    } else if (position == this.length - 1){
                        current = this.tail
                        this.tail.prev.next = null
                        this.tail = this.tail.prev
                    } else {
                        var index = 0
                        while(index++ < position){
                            current = current.next
                        }
                        current.prev.next = current.next
                        current.next.prev = current.prev
                    }
                }
                this.length -= 1
                return current.data
            }
            DoublyLinkedNode.prototype.remove = function(data){
                var current = this.head
                while(current){
                    if (current.data == data){
                        current.prev.next = current.next.next
                        current.next.prev = current.prev
                        return current.data
                    }
                    current = current.next
                }
                return -1

                //Another is getting index of the data and using method removeAt()
            }

            DoublyLinkedNode.prototype.isEmpty = function(){
                return this.length == 0
            }

            DoublyLinkedNode.prototype.size = function(){
                return this.length
            }
        }
        var doublyLinkedNode = new DoublyLinkedNode()
        doublyLinkedNode.append("aaa")
        doublyLinkedNode.append("bbb")
        doublyLinkedNode.append("ccc")
        console.log(doublyLinkedNode)

        doublyLinkedNode.insert(0, 111)
        doublyLinkedNode.insert(3, 222)
        doublyLinkedNode.insert(5, 333)
        console.log(doublyLinkedNode.toStr())

        // console.log(doublyLinkedNode.get(0))
        // console.log(doublyLinkedNode.get(3))
        // console.log(doublyLinkedNode.get(5))

        // console.log(doublyLinkedNode.indexOf(111))
        // console.log(doublyLinkedNode.indexOf(222))
        // console.log(doublyLinkedNode.indexOf(333))
        // console.log(doublyLinkedNode.indexOf(777))

        // doublyLinkedNode.update(0, 000)
        // doublyLinkedNode.update(1, "xxx")
        // doublyLinkedNode.update(2, "yyy")
        // console.log(doublyLinkedNode.toStr())

        // doublyLinkedNode.removeAt(0)
        // doublyLinkedNode.removeAt(3)
        doublyLinkedNode.remove(222)
        console.log(doublyLinkedNode.remove(444))
        console.log(doublyLinkedNode.toStr())
    </script>
</body>
</html>
```