### Set

The speciality of Set:

1. No order, so we cannot get element by its position.
2. No-repeated element.

### Set Calculation

1. Union (A And B)
2. Intersection (the repeated part of A and B)
3. Difference (The elements in A is not B and its repeated part)
4. Subset (A belongs to B)



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
        function Set(){
            this.items = {}

            Set.prototype.add = function(val){
                if (this.has(val)){
                    return false
                }
                this.items[val] = val
                return true
            }

            Set.prototype.has = function(val){
                return this.items.hasOwnProperty(val)
            }

            Set.prototype.getValues = function(){
                return Object.keys(this.items)
            }

            Set.prototype.clear = function(){
                this.items = {}
            }
            Set.prototype.size = function(){
                return Object.keys(this.items).length
            }

            Set.prototype.remove = function(val){
                if (!this.has(val)){
                    return false
                }
                delete this.items[val]
                return true
            }

            Set.prototype.union = function(BSet){
                var unionSet = new Set()
                var values = this.getValues()

                for(var i = 0; i < values.length; i++){
                    unionSet.add(values[i])
                }

                values = BSet.getValues()
                for(var i = 0; i < values.length; i++){ 
                    unionSet.add(values[i])   
                }
                return unionSet
            }

            Set.prototype.intersection = function(BSet){
                var intersectionSet = new Set()
                var values = this.getValues()

                for(var i = 0; i < values.length; i++){
                    var item = values[i]
                    if (BSet.has(item)){
                        intersectionSet.add(item)
                    }
                }
                return intersectionSet
            }

            Set.prototype.difference = function(BSet){
                var differenceSet = new Set()
                var values = this.getValues()

                for(var i = 0; i < values.length; i++){
                    var item = values[i]
                    if (!BSet.has(item)){
                        differenceSet.add(item)
                    }
                }
                return differenceSet
            }

            Set.prototype.subset = function(BSet){
                var subset = new Set()
                var values = this.getValues()
                for(var i = 0; i < values.length; i++){
                    var item = values[i]
                    if (!BSet.has(item)){
                        return false
                    }
                }
                return true
            }
        }
        var set = new Set()
        set.add(111)
        console.log(set.add(111))
        set.add(222)
        set.add(333)
        // console.log(set.getValues())

        
        // console.log(set.remove(111))
        // console.log(set.remove(111))

        // console.log(set.size())
        // set.clear()
        // console.log(set.size())
        var bSet = new Set();
        bSet.add(333)
        bSet.add(555)
        bSet.add(666)
        bSet.add(444)
        
        // console.log(set.union(bSet))
        // var intersectionSet = set.intersection(bSet)
        // console.log(intersectionSet.getValues())

        // var differenceSet = set.difference(bSet)
        // console.log(differenceSet.getValues())

        console.log(set.subset(bSet))
    
    </script>
</body>
</html>
```

