# Meaningful Names

1. **Use Intention-Revealing Names:**
	- Always take care with your names and change them when you find better one.
	- Good name will tell you why it exists, what it does, how it used.
	- If a name requires a comment, then the name does not reveal its intent.
2. **Avoid Disinformation:**
	- One the awful examples of disinformative names would be the use of lower-case `L` or uppercase `O` as variable names
3. **Make Meaningful Distinctions:**
	- It is not sufficient to add number series(`a1, a2, ...`) or noise words(`a, the, as, ...`), even though the compiler is satisfied. If names must be different, then they should also mean something different.
4. **Use Pronounceable Names**
	
5. **Use Searchable Names:**
	- Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.
	- Single letter names can only be used as local variables inside short methods. *The length of a name should correspond to the size of its scope.*
6. **Avoid Mental Mapping:**
	 - A loop counter may be named `i` or `j` or `k` (though never `l`) if its scope is very small and no other names can conflict with it. This is because those single-letter names for loop counters are traditional.
	 - One difference between a smart programmer and a professional programmer is that the professional understands that *clarity in king*.
7. **Class Names:**
	- Classes and objects should have noun or noun phrase names like `Customer`, `WikiPage`, `Account`, and `AddressParser`. Avoid words like `Manager`, `Processor`, `Data`, or `Info` in the name of a class. A class name should not be a verb.
8. **Method Names:**
	- Methods should have verb or verb phrase names like `postPayment`, `deletePage`, or `save`. Accessors, mutators, and predicates should be named for their value and prefixed with `get`, `set`, and `is` according to their context.
9. **Pick One Word per Concept:**
	- Pick one word for one abstract concept and stick with it. For instance, it's confusing to have `fetch`, `retrieve`, and `get` as equivalent methods in different classes.
10. **Don't Pun:**
	- Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun. for example word `add` can have two meanings. first like adding two numbers with each other, and second like add an item to a list.
11. **Use Solution Domain Names:**
	- Remember that the people who read your code will be programmers. So go ahead and use computer science (CS) terms, algorithm names, pattern names, math terms, and so far.
12. **Use Problem Domain Names:**
	- When there is no "programmer-eese" for what you're doing, use the name from the problem domain.
13. **Add Meaningful Context:**
	- Imagine that you have variables name `firstName`, `lastName`, `street`, `houseNumber`, `city`, `state`, and `zipcode`. Taken together it's pretty clear that they form an address. But what if you just saw the `state` variable being used alone in a method? would you automatically infer that it was part of an address?
