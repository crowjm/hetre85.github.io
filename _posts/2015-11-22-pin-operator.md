---
layout: post
title:  "Elixir Pin Operator"
date:   2015-11-22 21:20:00
excerpt: Pin operator lets you pattern match cool_dogs to fire_dogs without rebinding variables.
---

So in brushing up on some of the Elixir that I learned this Summer I had a renewed appreciation for the Pin Operator. The Pin Operator basically lets you pattern match without rebinding a variable. You can check out [elixir-lang.org](http://elixir-lang.org) to learn more about pattern matching.

So let's say we have the following list of atoms:

{% highlight elixir %}
cool_dogs_conditions = [:ice, :zone, :level_50]
{% endhighlight %}

<br>
And I also have the following list for `fire_dogs_conditions`:

{% highlight elixir %}
fire_dogs_conditions = [:hot, :zone, :level_20]
{% endhighlight %}

<br>
How can I pattern match the two variables without accidentally rebinding the variable on the left hand side? Clearly I can't just use `=` as that will rebind the left-hand side:

{% highlight elixir %}
iex> cool_dogs_conditions = fire_dogs_conditions
[:hot, :zone, :level_20]
{% endhighlight %}

<br>
So, let's pretend we didn't do that and instead let's use the Pin Operator to pattern match! The Pin Operator is this: ^. Just place it before the variable.

{% highlight elixir %}
iex> ^cool_dogs_conditions = fire_dogs_conditions
** (MatchError) no match of right hand side value: [:hot, :zone, :level_20]
{% endhighlight %}

<br>

Perfect! It didn't match! What would it look like on a proper match? Let's created `fire_dogs_duplicate` to find out:

{% highlight elixir %}
iex> fire_dogs_dupliate = [:hot, :zone, :level_20]
iex> ^fire_dogs_conditions = fire_dogs_duplicate
iex> [:hot, :zone, :level_20]

{% endhighlight %}

<br>

Perfect! It just returns the value of the variables being matched.

Thanks for reading about the Pin Operator!

Cheers

\- hetre85
