# luaguide
A beginner's guide to Lua.
### Description
A beginner's guide to Lua.

### Official Documentation
The official `Programming in Lua` (the most widely used Lua reference/guide) can be read [here](https://www.lua.org/pil/contents.html). It contains everything I cover in this guide and much more, like asynchronous Lua, their API, and tons of other useful reviews.

### Topics
* Disclaimers
* Comments
* Printing
* Variables
* Strings
* Numbers
* Tables
* Operators
* Math
* Statements
* Loops
* Functions
* Scoping
* Globals

# Guide
### Disclaimers
* `;` is not required in Lua and is practically ignored.
* `''` is the same thing as `""` in Lua. `''` doesn't stand for a character.
* Lua is a case sensitive language. `Lua` and `lua` are entirely different in the compiler's eyes.
* Lua also uses `elseif` and `else`.

### Comments
Comments in lua begin with `--`.
```lua
-- This is a regular comment.

--[[
  This is a multi-line comment.
  What's up?
]]
```

Comments can also have `=` between `[[`.
```lua
--[=[
  This is good for ignoring multi-line strings! (We will cover those later on).
  [[ meow ]]
]=]
```

Comments with `=` between the `[[` must have the same amount of `=` in the closing `[[`. You can have any amount of `=` between the `[[`.
```lua
--[====[
  This is valid!
]====]
```

### Printing
Printing is simply done by using `print()`.
```lua
-- We are printing a number here.
print(123)

--[[
  The console will return the following:
  123
]]
```

### Variables
Variables are initiated commonly using the keyword `local`. There are also globals, but we will cover those later on.
```lua
-- This is a nil, or null variable.
local hello_world = nil
```

The keyword `nil` stands for `undefined` or `null` in Lua.

### Strings
Strings can be enveloped using `""` or `''`.
```lua
-- This is a string.
local str = 'Hello, World!'

-- This is also a string.
local strtwo = "Hello, World!"
```

Lua has a string library as well. The library can be used using `:` or `.`. The `:` syntax will be covered later on in this guide.
```lua
-- This is subbing in Lua.
print(string.sub('Hello, World!' , 2)) -- This will print 'ello, World!'.

-- This is also subbing in Lua.
print(('Hello World'):sub(2)) -- This will also print 'ello, World!'.

-- This is a multi-line string in Lua.
local multistr = [[
What's up?
Nothing much!
Meow.
]]

--[=[
  Multi-line strings account for ALL whitespace. This means [[ hi]] will return ' hi'.
  Here's what I mean...
]=]

print([[
hi there
]]) -- Returns 'hi there' with new lines above it and under it.

-- However, this will look different.
print([[
  hi there
]]) -- Returns '  hi there' with new lines above it and under it.

--[[
  As you can see, the tabs were accounted for even if it was a string. This works universally throughout your code.
  Make sure to remember this when dealing with multi-line strings.
]]
```

If you want to concatenate strings (or numbers), you use the `..` operator.
```lua
print('Hello, ' .. 'World!')
```

In order to concatenate booleans into strings, you have to use `tostring()`, which will be covered further on.
```lua
print('Hello, ' .. tostring(true))
```

The string library and can be learned about further [here](https://www.lua.org/pil/20.html).

### Numbers
Numbers don't have a specified type like `float`, `int`, or `double`. You can simply pass them as a regular variable.
```lua
-- This is a number.
print(123)

-- This is also a number.
print(12.3)

-- You can define a number using the variable syntax.
local randnumber = 123
local randnumbertwo = 12.3
```

There is no current number library, if you're excluding the `math` library, which we will cover later on.

### Tables
Arrays in Lua, or lists depending on your previous experience, are called `tables`. They use the braces syntax.
```lua
-- This is a table.
local tbl = {'hi there!', 123, true}

-- Tables can contain any value, whether it's booleans, numbers, strings, or functions.
```

A table's index starts in `1`, which is not common in other languages.
```lua
local tbl = {1, 2, 3}

print(tbl[1]) -- Returns the number '1' in the console.
```

Lua supports string indexes too. Basically these are properties of a table that have strings as names.
```lua
local tbl = {
  ['my favorite color'] = 'blue',
  1,
  true,
  500
}

-- Now we are going to index the table using the string.
print(tbl['my favorite color']) -- Returns 'blue' in the console.
```

You can also index tables using `0`, but you'd do it like you'd index a table using strings.
```lua
local tbl = { [0] = 'sup', true, 123}

print(tbl[0]) -- Returns 'sup' in the console.
```

Lua also supports hash-tables, which are tables that contain its own variables (not to be confused with variables outside of the table).
```lua
-- Our variables.
local rvar = 1
local rstr = 'Hello, World!'

-- Our table.
local tbl = {
  our_rvar = rvar,
  our_rstr = rstr,
  my_favorite_artist = 'picasso'
}

-- You'd index it like this.
print(tbl.our_rvar)

-- Or like this.
print(tbl['our_rvar'])
```

There is also a table library. Table functions cannot be called using `:`, but can be directly called from the table library.
```lua
local tbl = {}

-- Inserting new properties into our table.
table.insert(tbl, 'hi')
table.insert(tbl, 'hello world ok')

-- Concatenating our table.
print(table.concat(tbl, '\n'))

--[[
  Your console will look like this:
  
  hi
  hello world ok
]]
```

More details on the table library can be read [here](https://www.lua.org/pil/2.5.html).

### Operators
Operators can range from logical operators to arithmetical operators. Here are the logical operators:
* `and` Checks if the previous and after statements are true.
* `or` Checks if the previous or the after statement is true.
* `not` Checks if the after statement is false.
* `~=` Checks if the previous and after values don't equal eachother.

Here are the arthmetical operators:
* `+` Addition
* `==` Comparison
* `-` Subtraction (or negativity)
* `/` Division
* `%` Modulo
* `*` Multiplication

Logical operators are used for conditions.
```lua
print(1 and 0) -- Returns true because both of these numbers exist.
print(not true) -- Prints false, which is the opposite of true.
print(not false) -- Prints true, since 'not' represents false.
```

Arithmetic operators are used for number manipulation or conditions.
```lua
print(true == true) -- Returns true because true does equal true.
print(1 == 0) -- Returns false because 1 doesn't equal 0.
print(1 / 0.5) -- Returns 2 because 1 divided by 0.5 equals 2.
print(500 - 100) -- Returns 400 because 500 subtracted by 100 equals 400.
```

### Math
The math library, or the keyword `math`, is used for... well.. math.
```lua
print(math.round(0.5)) -- Returns 1 because 0.5 rounds to 1.
print(math.abs(-60)) -- Returns 60 because the absolute value of -60 equals 60.
```

You can find more on the math library [here](https://www.lua.org/pil/18.html).

### Statements
Statements are created using logical operators. If statements, loops, and more are stopped/finished using the keyword `end`. Lua does not utilize braces or encasings for
loops or statements.

```lua
-- This is a simple if statement, which checks if the existence of 'istrue' is there, or if it has a value of true.
local istrue = true

if istrue then
  print('Istrue is a variable that exists, or is true.')
else
  print('Istrue doesn\'t exist, or is false.')
end
```

Now, onto more complex if statements...
```lua
-- This is a more complex if statment which involves math and more logical operators.
local intone = 1
local inttwo = 2
local intonecopy = intone

if (intone + inttwo) == 3 and intonecopy == intone then -- You don't have to surround the addition in parentheses, by the way. Lua can handle mathematical order.
  print('Intone and inttwo equal 3, while intonecopy is equal to intone.')
elseif (intone + inttwo) ~= 3 then
  print('That statement was excruciatingly false.')
end
```

### Loops
Lua features every loop you can think of, besides a `for (int)` (or more commonly known as `for (let)`) one. Loops are started by using the `do` keyword.
```lua
-- Here's a simple while loop.
local whilevar = true

while whilevar do -- This will continue until 'whilevar' is defined as false.
  print('Seems we\'re stuck in a loop!')
end
```

Now moving onto `repeat` loops. The difference between a `while` and `repeat` loop is that the `repeat` loop will run the condition at least once, whether the condition is false or not.
```lua
local repeatvar = true

repeat
  print('We\'re repeating this over and over, sighhhhhhh...')
until not repeatvar -- This loop will continue until 'repeatvar' is defined as false.
```

Then we have `for` loops. You can use these for tables, strings, and numbers. Strings are usually looped through using Lua expressions (or more commonly associated as regex).
```lua
-- Our table.
local tbl = {'welcome', 'to', 'hell'}

-- Looping through said table.
for i, v in pairs(tbl) do -- Pairs is for loops, just go with the flow.
  print(i, v) -- Returns the current index (1, 2, 3, etc.) and the value at that index (hence 'v').
end

-- You don't have to use 'i, v'. You can name 'i' using 'Index', or whatever you like.
```

Now we are going to try a numerical loop.
```lua
-- Looping from one number to the other number.
for i = 0, 5 do
  print(i) -- Returns 1, 2, 3, etc.
end

--[[
  Your console will look like this:
  
  1
  2
  3
  4
  5
]]
```

When it comes to tables, you can also loop through them using `ipairs`. It's a faster and more efficient way compared to `pairs`. However, `ipairs` will only scan only table values that aren't indexed using names/strings, like `['my favorite color']`, and will stop the loop if it comes upon a nil value, unlike `pairs`. Always use `ipairs` if you're comfortable with it. I switch from them 24/7 in my code.
```lua
-- Our table
local tbl = {
  ['123'] = true,
  5,
  6,
  false,
  nil,
  ['ok'] = false,
  'hello'
}

for i, v in ipairs(tbl) do
  print(i, v)
end

--[[
  Your console will look like this:
  
  5,
  6
  false
  
  That is because it is ignoring named indexes, as well as nil properties.
]]
```

### Functions
Functions, or sometimes named methods, are pretty self explanatory.
```lua
-- Initiating a local function.
local function hello_world(parameterone, parametertwo)
  print('Hello, ' .. parameterone .. ' and ' .. parametertwo)
end

-- You can also use this syntax.
local hello_world = function(parameterone, parametertwo)
  print('Hello, ' .. parameterone .. ' and ' .. parametertwo)
end
```

Within the global scope, which I'll explain later on, you can make functions for a table that use the `:` syntax. Normally functions from a table will be called using `.`.
```lua
local tbl = {}

-- Our globally scoped function.
function tbl:printrandomstuff()
  print('blah blah blah')
end

-- Calling the function.
tbl:printrandomstuff()
```

### Scoping
Lua has scoping syntax that is similar to commonly known scoping syntaxes.
```lua
if 1 == 1 then
  local var = 1
end

print(var) -- Returns nil, as that variable is a local that is initiated inside that if statement only. It only exists within that statement.
```

### Globals
In Lua, you can define globals that will be accessible, without requiring or putting them in a local, throughout the entire workspace. In every Lua project, there is a keyword that has the value of a table. The keyword is `_G`.
```lua
-- 'hello_world' is now available globally. _G works like a standard table, just with an exponentially larger scope.
_G.hello_world = 'Hello, World!'
```

Here's an example of scoping with `_G`.
```lua
if true then
  local randvar = 10
  
  _G.gvar = 10
end

print(randvar) -- Returns nil, as the local we created is only available inside the if statement.
print(gvar) -- Returns 10, as 'gvar' is now globally scoped.
```
