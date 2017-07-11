# Ruby Methods

## Objective
***Students will be able to create and use their own custom methods***

## SWBATS

+ METHODS - explain what a method is and why it's used
+ METHODS - use built in methods for each data type and structure
+ METHODS - chain methods together
+ METHODS - experiment and investigate unknown ruby methods using documentation and other 
+ internet resources
+ METHODS - explain what a return value is and what it's used for
+ METHODS - explain and determine the return value of a method
+ METHODS - explain what the return value of the puts method is
+ METHODS - differentiate between methods that puts and methods that return a value
+ SCOPE - explain that local variables cannot work between methods because of scope
+ METHODS - explain the difference between defining and calling a method
+ METHODS - call previously defined custom methods
+ METHODS - create a custom method using def and end key words
+ METHODS - use correct syntax in naming methods
+ METHODS - create a custom method using arguments

## Motivation

+ Coding becomes powerful when you start writing your own methods like the ones used to control the drone. Soon you will know enough about methods to create your own drone army.



+ A method is just a set of instructions that tells the computer to do something. They are awesome because they allow us to write code ONCE and then re-use it as many times as we want! 
	```
	Close your computer
	Put it in your bag
	Stand up
	Walk out the door
	```
+ We can encompass these instructions in a method called go_home
	+ You need to give really explicit instructions to a computer when you create a method (just like we did)
+ We use the following syntax to write a method and create a sort of code “block”:
```ruby
	def method_name
		your code goes here! 
	end
```
+ We use the keyword `def` to DEFINE the method, followed by the name of the method, then some code in the middle and the keyword end to tell the computer that this method is complete.
	+ Share an example: 
```ruby
def go_home 
	puts “Close your computer”
	puts “Put it in your bag”
	puts “Stand up”
	puts “Walk out the door” 
	puts “Go to your house”
end
```
+ Try saving this and running it. Nothing happens. 
+ Defining a method is like telling the computer how to do something, but then we need to also call the method to make the computer execute that code. 

+ Every method that we write gives us something called a return value - this is what Ruby evaluates for us and gives us back to use in other parts of our program. The return value of our methods is the last line evaluated. 
+ What would the return value of these methods be?
	```ruby
	def hello_world
		"Hello World"
	end # returns "Hello World"

	def one_plus_one
		1 + 1 
	end # returns 2 - ruby evaluates the line first
	```
+ A return value is always going to be the result of the last line of code in a method. So what's the return value of the following method:

```ruby
 def go_home 
	puts “Close your computer”
	puts “Put it in your bag”
	puts “Stand up”
	puts “Walk out the door” 
	puts “Go to your house”
end
```
+ Actually, it returns `nil`. Nil is Ruby's way to saying "nothing". Why would `puts 
+ `puts` is a method - and it’s only purpose is to print something to the screen. It doesn’t evaluate anything it just prints out and returns NOTHING or nil. So the last line of our program is calling the puts method - which prints something to the screen AND returns nothing or nil
+ Let’s look at another example
```ruby
def go_home
	puts “Go home!” 
	return “Go home!”
end
```
+ What will this method return? Ruby read (evaluated) the last line of code and returned it to us. We weren’t asking it to do anything so it just gave us back the string that was in the last line of code. 
+ Try deleting “Go home!” from the last line of the method and replacing it with 1+1. What was the return value? 
	+ The important thing to remember is that Ruby reads code from top to bottom and will ALWAYS return the result of the last line of code
	+ We actually don’t even need that word return. Ruby will automatically return that last line.
+ This is important because as you write more complex programs, one method may rely on the return value of another. 
+ Let’s take a look at chaining. You guys have already done chaining. Remember string methods? How we would take “i love ruby” and print it in all caps and backwards. upcase.reverse
+ The return value of upcase is important because reverse depends on it.
+ Let’s try chaining 

```ruby
def say_hello
	puts “hello!”
end 
say_hello.upcase
```
+ This doesn’t work! Why do we get this error message: `undefined method 'upcase' for nil:NilClass`
+ Because puts returns nil. How might we make this work? 
+ There are a ton of other pre-written Ruby methods like upcase and downcase that you can use. Different methods can be used on different data types. For example, you can use upcase on a string but not an integer or a float. They can be found [here](http://www.ruby-doc.org/core-2.1.1/) in the ruby docs: 
+ Show class how to search for classes and methods
+ Command F

```ruby
 def go_home 
	puts “Close your computer”
	puts “Put it in your bag”
	puts “Stand up”
	puts “Walk out the door” 
	puts “Go to your house”
end
```
+ What if we wanted to reuse some of these instructions but instead of sending a student home we want to send them out to grab us some lunch.
+ We can use something called an argument to feed them a location like this:

```ruby
def go_for_lunch(location)
	puts “Close your computer”
	puts “Put it in your bag”
	puts “Stand up”
	puts “Walk out the door” 
	puts “Go to #{location} to pick up lunch”
end
```
+ Where would you guys like to send out our student? ***Get a location from the class.***
+ Arguments allow us to pass information into a method and makes our code more flexible and reusable. 
+ Let’s do another example. What if I wanted to write a program that says hello to everyone in the classroom. Help me write this.

```ruby
def say_name(name) 
	puts “Hello #{name}!” 
end
```
And how would we call this? `say_name(“Vanessa”)`, `say_name(“Victoria”)`

+ When you call this method you can feed it any string that you want as the name - but remember it has to be a string.
+ Methods don’t always have to take in strings though. They can also take in numbers and multiple arguments at one time.
For example:
```ruby
	def many_pets(species, number)
		 “I love #{species}! I have #{number}!”
	 end
	 puts many_pets(“cats”, 5)
```

Or this:

```ruby
def addition(number_1, number_1)
	number_1 + number_2
end
puts addition(2, 3)
```

+ We can also set default values for our arguments like this:

```ruby
	def say_name(name="Programmer”) 
		puts “Hello #{name}!”
	end
```

Why do we have to feed arguments into a method anyway? Why can’t we do this:
+ What if instead of feeding in an argument for name we just defined name at the top of the file. Like this:

```ruby
	name = “Joe”
	def say_hello
	puts “hello #{name}”
	end
	puts say_hello
```
+ Let’s try running this file. 
+ What does this error message mean? `undefined local variable or method 'name'`
+ The method doesn’t recognize the variable name. That is because a method creates its own world. 

+ In this example the name variable lives outside of this world, so say_hello doesn’t even know it exists. Let’s try defining name inside of the method. This works!

```ruby
name = “Joe”
def say_hello
name = “Bob”
puts “hello #{name}”
end
```
+ Which name gets printed out though? Bob.
+ Now one more test. Let’s trying adding puts “hello #{name}” outside of our method at the bottom of the file. What do you think will be printed to the screen?

```ruby
name = “Joe”
def say_hello
name = “Bob”
puts “hello #{name}”
end
say_hello
puts “hello #{name}”
```
+ Why does it print both “Hello Bob” and “Hello Joe”? Why in that order?
+ What we just talked about is called scope. It is not so important for simple labs like the ones we are doing now, but it will become very important later. Don’t forget about scope! 
+ For now, just remember that you’ll need to feed information into a method with an argument. Otherwise your method will not know what you are talking about.
