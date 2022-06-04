# List

## Learning Goals

- Explain the List interface
- Use different implementations of the List interface

## List in Java

`List` is an `interface` in Java that takes advantage of the principles we
explored in the previous section. A "list" is something that has certain
capabilities, but Java does not provide a "base class" for lists. In other
words, there is no "default" implementation of "list" functionality. Instead,
there are specific implementations of the `List` interface that provide
implementations that are optimized for certain use cases:

1. `ArrayList`: this implementation focuses on the access speed for its data
2. `LinkedList`: this implementation focuses on the insertion and manipulation
   (moving) speed for its data
3. `Stack`: this implementation focuses on the ability to push elements on a
   stack and pop them from a stack in a last-in, first-out (LIFO) access pattern
4. `Vector`: this implementation is focused on making the underlying collection
   "thread safe", which means it can more easily be used by multiple "running
   instances of your program" at the same. "Multi-threading" will be covered in
   later unit.

The most important aspect of all these implementations is that because they all
implement the `List` interface, you could use them interchangeably for list
functionality. But because their implementations vary, it's good to understand
what use cases they are better suited for.

In this section, we will focus on general `List` functionality, and we will use
the most commonly used `List` implementation, `ArrayList` in our examples. But
all the examples we will be going through will work with any of the `List`
implementations.

The most important aspects of a `List` in Java are:

1. A list is an ordered data structure, which means that each element is added
   at a specific location and can be accessed using an index, which represents
   its position in the collection
2. Lists allow duplicates
3. A list is dynamically sized, which means it can continue to grow as you add
   elements to it
4. A list is part of the Java Collections framework, which gives it several
   capabilities that we will go over below

To use a `List` in Java, I must choose a specific implementation - in this case,
I will choose ArrayList:

```java
List myList = new ArrayList();
myList.add("a name");
myList.add(2);
myList.add(2.3);
for (Object item: myList) {
System.out.println(item);
}
myList.add("a fourth item");
System.out.println(myList.get(3));
```

As you can see, I was able to create my list without specifying how many items
it would hold and I was able to keep adding to the list without having to worry
about re-sizing it.

I can refer to any item on the list by its index: `myList.get(<index>);`. Note
that, as with arrays, indexes on lists are 0-based.

I was also able to add objects of any kind to this list. This is not necessarily
a good thing:

1. Although it's convenient to be able to put anything on my list, it makes
   using any of those values difficult because I don't know their type, which
   means I can't be sure what I'm allowed to do with them and what I'm not
2. This is not "type safe", which means the compiler has no way to tell me if
   I'm adding something to my list that wasn't meant to be there

This is where generics come into play: we can change our list definition to
specify what type of items we want in the list because lists in Java support
generics:

```java
List<String> myStringList = new ArrayList<String>();
myStringList.add("first string");
myStringList.add("second string");
myStringList.add("third string");
for (String myString: myStringList) {
    System.out.println(myString);
}
```

This `String` list will now only accept `String` objects and the compiler will
be not accept any other values.

Here are the key methods of the `List` class:

1. Add an item: `myStringList.add("Sample String");`
2. Get an item by index: `myStringList.get(0);`
3. Set the value for an item by index:
   `myStringList.set(0, "A new value for my sample string");`
4. Remove an item from the list by index: `myStringList.remove(0);`
   1. This resizes the list and shuffles all the elements after the item being
      removed by `currentIndex - 1`
5. Remove all elements in a list: `myStringList.clear();`
6. Get the current size of a list: `myStringList.size();`
7. Check if the list contains a specific element:
   `myStringList.contains("Sample String");` - returns a boolean
8. Check if the list contains all the elements in the specific collection:
   `myStringList.containsAll(myList);` - returns a boolean
9. Sort a list using the Collections' framework default sorting method:
   `Collections.sort(myStringList);`

Looping through an array list is the same as looping through a regular array.
