---
layout: post
title:  "Elixir Nested Maps"
date:   2015-08-27 21:45:00
excerpt: Maps are key/value collections, great for storing cool_dogs
---

So far, I have made it through the [elixir-lang](http://elixir-lang.org) getting started guide and about 30 pages into [Programming Elixir](https://pragprog.com/book/elixir/programming-elixir). It's definitely been good to go over the material again since I don't have a lot of experience with functional programming. I went back over collections today.

Elixir has several collections including Tuples, Lists, Keyword Lists, Maps, and Binaries. To be honest I am trying to think about these ideas in terms of their own usage and existence as opposed to simply viewing them by analogy to things that I am already familiar with.

Maps are key/value collections, great for storing cool_dogs and other stuff. Their syntax looks like this:

    %{:key => value}

<br>
If all the keys are atoms (the ones with a leading colon) you can use this shortcut syntax and it feels eerily similar to Ruby.

     %{key: value, k: v}

<br>
This seems very familiar and is really easy to work with. Here is an example of a nested Map:

    cool_dogs = %{ dogs: %{ john: %{age: 1, ears: "pointy"}, donut: %{age: 4, ears: "floppy"}}}

<br>
Yay! Now we have a list of cool_dogs. If we want to access the value of the the atom `:dogs`, we can use our old friend square bracket to get there:

    iex> cool_dogs[:dogs]
    %{donut: %{age: 4, ears: "floppy"}, john: %{age: 1, ears: "pointy"}}

<br>
We can go further any by supplying another set of square brackets:

    iex> cool_dogs[:dogs][:donut]
    %{age: 4, ears: "floppy"}

<br>

And if you totally zone out and throw in a key that does not exist:

    iex(8)> cool_dogs[:legends_of_the_hidden_temple][:olmec][:open_your_temple_gates]
    nil

<br>

Instead of having to run away from the Temple Guardians, Elixir just returns `nil`. And that's what I like about Elixir :)

Tomorrow I'm going to go back over Anonymous Functions. See you next time!

Cheers

\- hetre85




