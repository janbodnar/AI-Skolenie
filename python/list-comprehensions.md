# Python list comprehensions

A *list comprehension* is a syntactic construct that creates a new list from an existing  
sequence or iterable. List comprehensions provide a concise way to build lists. A common task  
is to make a new list where each element is the result of some operation applied to each member  
of another iterable, or to create a subsequence of the elements that satisfy a certain condition.

A list comprehension can be used to:

- transform a list
- filter a list

The syntax of list comprehensions was influenced by the mathematical set-builder notation.  
Python borrowed the construct from the Haskell programming language.

```math
S = \{x^2 : x \in \{0, 1, \dots, 16\}\}
```

This is the mathematical notation for a set of the squares of the integers 0 through 16.  
The Python equivalent is very close to it:

```python
S = [x ** 2 for x in range(17)]
```

The general form of a list comprehension is:

```python
[expression for item in iterable if condition]
```

It consists of three parts: an expression, a `for` clause, and an optional `if` clause.  
The `for` clause goes through the iterable. In each iteration, the condition is tested; if it  
is met, the expression is evaluated and its value is appended to the new list. A list  
comprehension can contain multiple `for` and `if` clauses.

A list comprehension is a shorter form of the following loop:

```python
result = []
for item in iterable:
    if condition:
        result.append(expression)
```

## Transforming a list

The following example transforms a list into another list with a list comprehension.

```python
a = [1, 2, 3, 4, 5, 6]

b = [e * 2 for e in a]
print(b)
```

We create a new list from an existing list by multiplying each element by 2.

```python
b = [e * 2 for e in a]
```

Each element of the `a` list is multiplied by 2 and the result is added to the new `b` list.

```
$ python multiply_elements.py
[2, 4, 6, 8, 10, 12]
```

Each of the elements was multiplied by two.

## Celsius to Fahrenheit

We have a list of temperatures in Celsius. We want to create a new list of temperatures expressed  
in Fahrenheit.

```python
celsius = [22, 28, 33, 42, 52]

fahr = [e * 9 / 5 + 32 for e in celsius]
print(fahr)
```

The example creates a new list of Fahrenheit temperatures calculated from a list of Celsius  
temperatures.

```python
fahr = [e * 9 / 5 + 32 for e in celsius]
```

The calculation is done in the expression part of the list comprehension.

```
$ python celsius_to_fahrenheit.py
[71.6, 82.4, 91.4, 107.6, 125.6]
```

## Filtering a list

In the following example, we filter a list with a list comprehension.

```python
a = [-4, 2, 0, -1, 12, -3]

b = [e for e in a if e > 0]
print(b)
```

We have a list of integers. We create a new list that includes only the positive integers.

```python
b = [e for e in a if e > 0]
```

The `if` condition is applied to each of the elements; an element is included in the new list  
only if it satisfies the condition.

```
$ python filter_positive.py
[2, 12]
```

The next example filters elements by their type.

```python
a = ['a', 2, 'c', 12, 3, 'd']

b = [e for e in a if isinstance(e, int)]
c = [e for e in a if isinstance(e, str)]

print(b)
print(c)
```

We have a list of integers and strings. We create two new lists; one contains only integers  
and the other only strings.

```python
b = [e for e in a if isinstance(e, int)]
```

Here we create the `b` list, which contains only integer values. The built-in `isinstance`  
function checks the type of the element. It is preferred to comparing `type(e) == int`  
because it also accepts subclasses. Note that `bool` is a subclass of `int`, so `True` and  
`False` would pass this filter too.

```
$ python filter_by_type.py
[2, 12, 3]
['a', 'c', 'd']
```

## Predicates

A *predicate* is a function that returns a boolean value. If the condition is too complex,  
we can move it into a predicate.

```python
def is_vowel(c):
    return c.lower() in 'aeiou'


sentence = 'There are eagles in the sky.'

vowels = [c for c in sentence if is_vowel(c)]
print(vowels)
```

The example picks out all vowels from a sentence.

```python
def is_vowel(c):
    return c.lower() in 'aeiou'
```

The function is a predicate. It returns `True` for a vowel character. Calling `lower`  
makes it work for uppercase vowels as well.

```python
vowels = [c for c in sentence if is_vowel(c)]
```

The logic of the `if` condition is delegated to the `is_vowel` predicate.

```
$ python predicate.py
['e', 'e', 'a', 'e', 'e', 'a', 'e', 'i', 'e']
```

## Conditional expression in front

An `if`/`else` can also be placed in front of the `for` clause. This is not a filter but a  
conditional expression (`x if condition else y`); it is part of the expression and decides  
which value is added for each element. The `else` part is mandatory here.

```python
data = ['even' if i % 2 == 0 else 'odd' for i in range(7)]
print(data)
```

In the example, we transform the values into `'even'` and `'odd'` strings.

```
$ python even_odd.py
['even', 'odd', 'even', 'odd', 'even', 'odd', 'even']
```

The two forms can be combined. In the next example, the conditional expression replaces  
negative values with zero, while the trailing `if` drops the `None` values.

```python
a = [-4, 2, None, -1, 12, None, -3]

b = [e if e > 0 else 0 for e in a if e is not None]
print(b)
```

The filter runs first, so the conditional expression never sees `None`.

```
$ python clamp_values.py
[0, 2, 0, 12, 0]
```

## Multiple if conditions

A list comprehension can have multiple `if` clauses.

```python
a = [9, 2, 18, 14, 22, 11, 7, 19, 23]

b = [e for e in a if e > 10 if e < 20]
print(b)
```

We create a new list of the integers from list `a` that are greater than 10 and lower than 20.

```python
b = [e for e in a if e > 10 if e < 20]
```

In this list comprehension, we use two `if` clauses. An element must satisfy all of them.  
The same can be written more idiomatically with a chained comparison:  
`[e for e in a if 10 < e < 20]`.

```
$ python multiple_conditions.py
[18, 14, 11, 19]
```

## Multiple for loops

A list comprehension can have multiple `for` clauses. They are nested in the same order  
as they would be in regular `for` loops.

```python
a = [1, 2, 3]
b = ['A', 'B', 'C']

c = [str(i) + j for i in a for j in b]
print(c)
```

The example creates a Cartesian product of two lists.

```python
c = [str(i) + j for i in a for j in b]
```

Two `for` clauses are used to create a Cartesian product. The first one is the outer loop.

```
$ python multiple_for_loops.py
['1A', '1B', '1C', '2A', '2B', '2C', '3A', '3B', '3C']
```

The next example shows how to flatten a nested list.

```python
nums = [[1, 2, 3], [3, 4, 5], [6, 7, 8]]

c = [e for row in nums for e in row]
print(c)
```

The `nums` list is a list of nested lists. We flatten it with a list comprehension.

```python
c = [e for row in nums for e in row]
```

The first `for` clause goes through the outer list; the second goes through each nested list.

```
$ python flatten_list.py
[1, 2, 3, 3, 4, 5, 6, 7, 8]
```

## Cards

In the following example, we create a deck of cards, shuffle it, and deal it into four  
hands with list comprehensions.

```python
import random

ranks = [2, 3, 4, 5, 6, 7, 8, 9, 10, 'J', 'Q', 'K', 'A']
suits = ['♣', '♦', '♥', '♠']

deck = [f'{rank}{suit}' for suit in suits for rank in ranks]
random.shuffle(deck)

hands = [deck[i:i + 13] for i in range(0, len(deck), 13)]

for hand in hands:
    print(' '.join(hand))
```

First, we combine every rank with every suit to get the 52 cards.

```python
deck = [f'{rank}{suit}' for suit in suits for rank in ranks]
```

The f-string builds a card name such as `'10♥'` or `'Q♠'`.

```python
hands = [deck[i:i + 13] for i in range(0, len(deck), 13)]
```

After shuffling the deck, we partition it into four hands of 13 cards. The `range` function  
generates the starting index of each hand: 0, 13, 26, and 39. Since Python 3.12, the same can  
be done with `itertools.batched(deck, 13)`, which yields tuples.

```
$ python cards.py
4♣ 7♣ 2♣ 9♥ K♦ 5♠ 6♠ 5♣ 10♠ 7♠ 7♥ 2♠ 9♠
5♥ 9♣ 3♥ 10♥ A♣ Q♥ 8♣ 4♠ 8♠ K♠ 4♦ J♥ 2♥
J♦ 3♦ 3♣ 4♥ 3♠ 9♦ K♣ 7♦ K♥ A♠ 10♣ Q♠ 6♦
8♦ Q♦ J♣ J♠ 6♥ 8♥ 5♦ 6♣ 2♦ 10♦ A♦ Q♣ A♥
```

The output is different each time because the deck is shuffled.

## Nested list comprehensions

The expression in a list comprehension can be another list comprehension.

```python
M1 = [[1, 2, 3],
      [4, 5, 6],
      [7, 8, 9]]

M1_tr = [[row[i] for row in M1] for i in range(len(M1[0]))]
print(M1_tr)
```

The example defines a matrix and creates its transpose with a nested list comprehension.  
The outer comprehension goes through the column indexes; the inner one picks the element at  
that index from each row. The idiomatic alternative is `[list(col) for col in zip(*M1)]`.

```
$ python transpose_matrix.py
[[1, 4, 7], [2, 5, 8], [3, 6, 9]]
```

## Assignment expressions

Since Python 3.8, the walrus operator `:=` can be used in a list comprehension. It assigns the  
result of an expression to a name, so that a value computed in the condition can be reused in  
the output expression without computing it twice.

```python
import math

vals = [1, 4, 7, 9, 15, 16, 20, 25]

roots = [r for v in vals if (r := math.isqrt(v)) ** 2 == v]
print(roots)
```

The example finds the perfect squares in the list and keeps their square roots.

```python
roots = [r for v in vals if (r := math.isqrt(v)) ** 2 == v]
```

The integer square root is computed once in the condition, bound to `r`, and then used  
as the value of the new element.

```
$ python walrus.py
[1, 2, 3, 4, 5]
```

## Variable scope

A list comprehension has its own scope. Its loop variable does not leak into the surrounding  
code and does not overwrite a variable with the same name.

```python
x = 'outer'

vals = [x * 2 for x in range(4)]

print(vals)
print(x)
```

The `x` used inside the comprehension is a separate variable.

```
$ python scope.py
[0, 2, 4, 6]
outer
```

The `x` variable kept its original value. The exception is the walrus operator: a name bound  
with `:=` inside a comprehension is assigned in the enclosing scope.

## Sieve of Eratosthenes

The Sieve of Eratosthenes is an ancient algorithm for finding prime numbers. A prime number  
is a natural number greater than 1 that has no positive divisors other than 1 and itself.  
The algorithm iteratively marks as composite (i.e., not prime) the multiples of each number,  
starting with the multiples of 2.

```python
import math

n = 100

no_primes = {j for i in range(2, math.isqrt(n) + 1) for j in range(i * i, n, i)}
primes = [e for e in range(2, n) if e not in no_primes]

print(primes)
```

The example computes the prime numbers below 100. It is a compact illustration of the sieve  
idea rather than an efficient implementation.

```python
no_primes = {j for i in range(2, math.isqrt(n) + 1) for j in range(i * i, n, i)}
```

First, we create the composite numbers. It is enough to go up to the square root of `n`,  
because every composite number below `n` has a divisor no greater than that. The marking  
can start at `i * i`, since smaller multiples of `i` were already marked by smaller numbers.  
We use a set comprehension (curly brackets) because checking membership in a set is much  
faster than in a list.

```python
primes = [e for e in range(2, n) if e not in no_primes]
```

The prime numbers are the numbers that are not in the `no_primes` set.

```
$ python sieve_of_eratosthenes.py
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97]
```

## Related comprehensions

The same syntax is available for other types. A set comprehension uses curly brackets,  
a dictionary comprehension uses curly brackets with a `key: value` expression, and  
a generator expression uses round brackets.

```python
words = ['sky', 'cloud', 'rock', 'sky', 'forest', 'cloud']

unique = {w for w in words}
lengths = {w: len(w) for w in words}
total = sum(len(w) for w in words)

print(unique)
print(lengths)
print(total)
```

A generator expression does not build a list in memory; it produces the values one by one.  
When the result is passed directly to a function such as `sum`, `max`, `any`, or `all`,  
the extra brackets can be omitted.

```
$ python related.py
{'rock', 'cloud', 'forest', 'sky'}
{'sky': 3, 'cloud': 5, 'rock': 4, 'forest': 6}
26
```

The order of the elements in a set is arbitrary and can differ between runs.

## When not to use a list comprehension

List comprehensions are meant for building lists. Avoid using them only for side effects:

```python
# don't do this
[print(e) for e in vals]

# use a regular loop instead
for e in vals:
    print(e)
```

The first form creates a useless list of `None` values. Also, when a comprehension grows to  
several `for` and `if` clauses, a regular loop or a helper function is usually easier to read.

## Source

[Python tutorial: List comprehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions)

In this article we have worked with Python list comprehensions.
