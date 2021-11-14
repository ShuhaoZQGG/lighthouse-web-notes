### [Compass](https://web.compass.lighthouselabs.ca/days/w08d5)

### [Instructor's Notes](https://web.compass.lighthouselabs.ca/activities/405/lectures/4898)

### [Today's Work](https://github.com/ShuhaoZQGG/learn_ruby)

[Benchmark_with_Blocks](https://gist.github.com/ShuhaoZQGG/8de5522a7355d724e7b0c124785aa6dd) (refer it for understanding blocks and yield (yield is similar to callback))

[Candidates](https://gist.github.com/ShuhaoZQGG/a359802c567075ca3a3771ed88dd24b9) (Gist for understanding ruby hash)

# Ruby Syntax

## ruby's "print", "console log":

```ruby
puts "string"
p "string"
pp "string"

# puts return whatever you typed into .to_s method (aka transfer into string)
# p return the raw object that passed into it because it uses .inspect method under the hood
# pp similar to p instead it returns hashes and arrays to a more readable format
```

## Get prompt (command line input argument) in ruby:

```ruby
print "Give me a number: "
number = gets.chomp.to_i
```

## **Ruby's variable:**

```ruby
# AS you may notice, ruby doesn't explicitly assign types to its variables like JS

string = "i am a string"
string_num = "1"
number = string_num.to_i
array = [1,2,3]
hash = {key1: 1, key2: 2, key3: 3} #in JS it's object but in ruby it's hash
```

## Unpacking Variables in string:

```ruby
my_name = "zsh"
puts "My name is #{my_name}"

# In JS we use string literal `` and dollar sign ${}
# In Ruby we use double quotes "" and pong #
```

## Function

```ruby
def print_one(arg1)
  puts "arg1: #{arg1}"
end

def add (x, y)
	x + y
end

def return(x)
	return x
end

# there must be an "end" at the end of each expression (after function, if/else, while
# /for, etc). 

# if there is no explicit return, ruby will take the last line before end as its default 
# return value 
 
```

## if/elsif/else:

```ruby
people = 30
cars = 40
trucks = 15

if cars > people
  puts "We should take the cars."
elsif cars < people
  puts "We should not take the cars."
else
  puts "We can't decide."
end

# "end" at the end of every if/elsif/else expression
# elsif 
```

## Many for loop options (confusing part):

```ruby
the_count = [1, 2, 3, 4, 5]
fruits = ['apples', 'oranges', 'pears', 'apricots']
change = [1, 'pennies', 2, 'dimes', 3, 'quarters']

# this first kind of for-loop goes through a list
# in a more traditional style found in other languages
for number in the_count
  puts "This is count #{number}"
end

# same as above, but in a more Ruby style
# this and the next one are the preferred 
# way Ruby for-loops are written
fruits.each do |fruit|
  puts "A fruit of type: #{fruit}"
end

# also we can go through mixed lists too
# note this is yet another style, exactly like above
# but a different syntax (way to write it).
change.each {|i| puts "I got #{i}" }

# we can also build lists, first start with an empty one
elements = []

# then use the range operator to do 0 to 5 counts
(0..5).each do |i|
  puts "adding #{i} to the list."
  # pushes the i variable on the *end* of the list
  elements.push(i)
end

# now we can print them out too
elements.each {|i| puts "Element was: #{i}" }
```

## While loop (more like JS):

```ruby
i = 0
numbers = []

while i < 6
  puts "At the top i is #{i}"
  numbers.push(i)

  i += 1
  puts "Numbers now: ", numbers
  puts "At the bottom i is #{i}"
end

puts "The numbers: "

# remember you can write this 2 other ways?
numbers.each {|num| puts num }
```

## Accessing elements of a Hash:

```ruby
# Hash is the ruby version of Object in JS
favorites = {
    books: ["Paris guidebook", "The Art of Innovation"],
    fruits: ["apples", "oranges", "pears"],
    colors: ["yellow", "green"],
}

state_capitals = {
    new_york: "Albany",
    pennsylvania: "Harrisburg",
    colorado: "Denver",
    maine: "Augusta",
    vermont: "Montpelier"
}

user = {
    first_name: "Emily",
    last_name: "Reese",
    age: 28,
    address: "123 Imaginary Road, New York, NY, 10014",
    picture: "photo.png",
    profile_quotes: ["If you can dream it, you can do it!", "Good vibes only."]
}

state_capitals[:new_york]
=> "Albany"

favorites[:books]
=> ["Paris guidebook", "The Art of Innovation"]

favorites[:books][0]
=> "Paris guidebook"
```

# Command lines for Ruby:

```ruby
# left is JS command and right is the corresponding ruby command
node -v  <=> ruby -v
node <=> irb
npm install <=> bundler install
nvm <=> gem
```