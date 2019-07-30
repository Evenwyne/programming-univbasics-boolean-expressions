# Boolean Expressions

## Learning Goals

* Use Equality Comparison
* Use Inequality Comparison
* Use Greater-Than Comparison `>`
* Use Less-Than Comparison `<`
* Use Greater-Than-or-Equal-To Comparison `>=`
* Use Less-Than-or-Equal-To Comparison `<=`
* Invert Truth Value with "Bang" (`!`)
* Invert Truth Value with "Double-Bang" (`!!`)
* Identify Truthy and Falsey Values in Ruby
* Join Boolean Expressions with AND
* Join Boolean Expressions with OR

## Introduction

As we saw in the ternary expression, sometimes we need to get a Boolean value
(`true` or `false`) _from another_ expression in order to use it _in_ another
expression.  In the previous lesson, we showed that we can use the greater-than
operator (`>`) and less-than operator (`<`) to perform comparisons that produce
or _calculated_ `true` or `false`. Let's get more operators so that we can gain
more expressions that return `true` or `false`.

## Arithmetic Comparisons

### Use Equality Comparison

To check whether two values are equal, we use the *equality operator* represented
with `==` ("double-equal-sign"). If two values are equal, then the statement
will return `true`. If they are not equal, then it will return `false`. For
example:

```ruby
1 == 1 #=> true

1 == 7 #=> false
```

**IMPORTANT**: We said this before, but it bears repeating, the comparison
operator `==` _is not the same as the assignment operator_ `=`, which is used
to assign values to variables. Mistaking these for each other is a common cause
of unexpected behavior (that is, a bug).

Now, this might feel a bit weird, because you're used to thinking about `=` or
`==` only being around numbers like `Integer` and `Float`. But you can also
compare `String`s:

```ruby
"Razz" == "Matazz" #=> false

"Poodle" == "Poodle" #=> true

"Poodle" == "poodle" #=> false
```
### Use Inequality Comparison

To check whether two values **are not** equal, we use the *inequality operator*
represented with `!=` (which programmers pronounce as "bang-equal-sign;" more
on "bang" below). If two values are not equal, then the statement will return
`true`. If they are equal, then it will return `false`. For example:

```ruby
1 != 1 #=> false

1 != 7 #=> true

"Poodle" != "Lord of the Manor" #=> true
```

## Quantity Comparisons

You might recall these from school: comparisons of greater-than versus
greater-than-or-equal-to.

### Use Greater-Than Comparison `>`

If the value on the left of the operator is *greater than* the value on the
right, then the evaluation is `true`; `false` otherwise.

### Use Less-Than Comparison `<`

If the value on the left of the operator is *less than* the value on the
right, then the evaluation is `true`; `false` otherwise.

### Use Greater-Than-or-Equal-To Comparison `>=`

If the value on the left of the operator is *greater than or equal to* the
value on the right, then the evaluation is `true`; `false` otherwise.

### Use Less-Than-or-Equal-To Comparison `<=`

If the value on the left of the operator is *less than or equal to* the
value on the right, then the evaluation is `true`; `false` otherwise.

## Invert Truth Value with "Bang" (`!`)

The `!` operator inverts a truth value. Here's the most simple version:

```ruby
!true #=> false
!false #=> true
```

We can also invert the truth value of an expression:

```ruby
( 1 + 1 == 2 ) #=> true
!( 1 + 1 == 2 ) #=> false
```

Since `1 + 1` evaluates to `2`; and since `2 == 2` the return value is `true`.

## Invert Truth Value with "Double-Bang" (`!!`) Part 1

The `!!` operator inverts a truth value. Here's the most simple version:

```ruby
!!true #=> true
!!false #=> false
```

We can also invert the truth value of an expression:

```ruby
!!( 1 + 1 == 2 ) #=> true
```

Now why would this ever be useful? Great question. To address this we need to
take a slight tangent to discuss what counts as `true` and `false` in Ruby.

## Truthiness in Ruby 

Ruby will treat a whole bunch of values as `true` that aren't the literal
`true`. We call those values "truthy." Similarly, there are values that, even
if they aren't the literal `false`, Ruby treats as false. We call those values
"falsey."

This next statement is ***very important***:

> **IMPORTANT**: Ruby will treat anything that is `false` or `nil` as `false`,
> but ***everything*** else as `true`.

So:

```ruby
false ? true : false  #=> false
nil   ? true : false  #=> false
6.7   ? true : false  #=> true
1 + 1 ? true : false  #=> true
:i_once_saw_a_poodle_play_racquetball ? true  : false  #=> true
```

Let's return to "double-bang."

## Invert Truth Value with "Double-Bang" (`!!`) Part 2

In each of the examples above, we wanted to return whether the `truthy` or
`falsey` value was a real-deal `true` or `false`. What a lot of code to type.
But here's where our friend the double-bang operator comes in.

```ruby
!!false #=> false
!!nil   #=> false
!!6.7   #=> true
!!1 + 1 #=> true
!!:i_once_saw_a_poodle_play_racquetball #=> true
```

Programmers often use double-bang to show other programmers "Hey, I'm being
clever here and am using a truthy value.

> **What's with "Bang?"** Programmers, being lazy people, thought that
> "exclamation point" was too long to say, so it became "bang." From this, many
> of the punctuation marks, since they're often used in code or systems
> administration, got cute nicknames. The `@` became "at" mostly to distinguish
> it from "ampersand" (`&`) which is often called "and." The octothorpe (`#`)
> became called "hash" or "pound" and thus the "hash-tag" of the social media
> era is a tag after, well, a "hash." "Splat" or "star" are common for `*` and
> we've heard `$` called "bling." "Caret" (`^`) and "percent" (`%`) don't seem
> to have clever names.

## Identify Truthy and Falsey Values in Ruby

This concept is ***so*** important we're going to repeat it again here:

> **IMPORTANT**: Ruby will treat anything that is `false` or `nil` as falsey
> all other things, even things you've not heard of yet are treated as truthy

## Join Boolean Expressions with AND

In Ruby `&&` ("double-ampersand") represents "AND." For an `&&` ("and") to
evaluate to `true`, both values of either side of the symbol must evaluate to
`true`. For example:

```ruby
true && true #=> true

true && false #=> false
```

It's common to say things like:

"IF it's Thursday AND my Mom is not home THEN I will play scary video games all
night on the living-room TV."

In Ruby we would express this "double-conditional" like so.

```ruby
day_is_thursday = true
mom_is_not_home = true
# Ternary
# Position 1                         # Position 2               # Position 3
day_is_thursday && mom_is_not_home ? "play scary video games" : "do homework"
```

## Join Boolean Expressions with OR

In Ruby `||` ("double-pipe") represents "OR." For an `||` ("or") to evaluate to
`true`, _only one_ value on either side of the symbol must evaluate to `true`.
For example:

```ruby
false || true #=> true
```

Of course, keep in mind, these Boolean values can, themselves, be expressions
that return a Boolean value!  Instead of `false && true` it could another
expression that results in `true` or `false` like `(poodle_count > 12) &&
(owner == "Lorlei Gilmore")`

## Longer Expressions

Because of the ability to use parentheses `()`, "and" (`&&`), "or" (`||`), and
the ternary expression, we can create surprisingly rich programs:

```ruby
chance_of_precipitation = 1000
temperature = -1000
it_is_wet = ( chance_of_precipitation > 0.5 )
it_is_cold = ( temperature <= 5 )
it_is_wet && it_is_cold ? "snow-suit" : "something less bulky" #=> "snow-suit"
it_is_wet && !it_is_cold ? "umbrella" : "light fabric"
```

Try typing this program into IRB and then change some of the values or
expressions to make sure you understand how to _express_ your ideas using
variables and Boolean conjunctions! Use your imagination to imagine simple bits
of conditional reasoning and try to get IRB to print out the right result. You
should feel like the conversations you're having with IRB are growing steadily
richer.

## Conclusion

While it might seem strange that these simple little conditional expressions
are so tiny, stacked together, they can have a big impact!

Most social media sites have a bit of conditional logic **just like this one**.

```ruby
top_corner_image = (user_logged_in && profile_pic_uploaded) ? retrieve_profile_pic : default_avatar
```

You should be able to reason about how you might ensure the `top_corner_image`
is your lovely face versus a default image.

## Conclusion

With this collection of comparison operators, you're able to express a
surprisingly complex series of desires to Ruby! Your programming conversational
level is nearing the pre-teen stage!
