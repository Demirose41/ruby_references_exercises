# Scope 
Scope describes the location in your program where a variable is accessible.

## Methods and Local Scope
To start we will explore **lexical scope**. 

Lexical scope describes how variable name evaluates in nested code. How variable names resolve if we put them in structures like methods, conditionals, or blocks.

In ruby it is important to note that a variable declared outside of a method can not be referenced within the scope of said method unless passed in.

ex.
```
message = "hi"

def say_hello
    p message # NameError: undefined local variable
end

say_hello
```

## Global Variables
Global scope refers to the everywhere area in our code that can be accessed from anywhere. To define a variable within the global scope we must precede the variable name with a "$". 

ex. 
```
$message = "hi"

def say_hello
    p $message 
end

say_hello # => "hello globe"
```

## Constants 
A constant is denoted snytactically by beginning the name with a capital letter. By convention we like to make the entire name capital to emphasize it being a special constant.
As always, constants may not be reassigned.

```
FOOD = "pho"
p FOOD # => "pho"

FOOD = "ramen" #warning: already initialized constant FOOD
               #Warning: precious definition of FOOD was here
```

!! Note. While we can not reassign a constant, we can still mutate it.
```
FOOD = "pho"
FOOD[0] = "P"
p FOOD # => "Pho
```
!!Note. Constant variables will also be stored in the global scope.

## What does not have it's own scope?

BLOCKS!!! Blocks do not have their own scope, they are really a part of the containing method's scope. 

Other conditionals or while loops also don't have their own scope, they are really part of the containing scope.

# References 
- .object_id will tell us a variables location in memory
- if we declare two seperate variables "word_1" and "word_2" and set them both to "boot" they will have different locations in memory 
- if we wanted word_1 and word_2 to point to the same value and position we would want to assign word_1 to word_2 like so "word_2 = word_1"
- by doing this an changes to the value of word_1 will reflect on word_2 becouse they both point to the same value in memory
- when reassigning a variable we will change its location in memory
## Array instantiation
- say we wanted to make a 3-dimensional array for a tic-tac-toe project. we could do so as such...
`grid = Array.new(10,Array.new(3)) # => [[nil,nil,nil],[nil,nil,nil],[nil,nil,nil]]`
- doing so will run into some troubles such as...
- if we wanted to change the value of say, grid[0][0] from nil to "X" we will end up with
`[["X",nil,nil],["X",nil,nil],["X",nil,nil]]`
- this occurs because of how we instantiated the array. We basically made each of the sub-arrays point towards our singular nested template array 
- Ruby does allow us to work around this though...
`grid = Array.new(3) { Array.new(3) }` 
- By rapping the sub-array within a block we will evaluate the block each time.