# Strategy
- It's a behavioral design pattern.
## Problem
Think you have a routing app, which shows the fastest way from point A to point B and currently just works for cars. In future you may want to add new features such as plane, walking, bike, public transport routes to your app.
In this case the main login is same we want a class `Router` that has a function `build_route(A, B)` and it returns the fastest way.
## Solution
We add `set_stratege` to our `Router` class that get's the strategy from user and then builds routes.


## Use Cases
1. Use the Strategy pattern when you want to use different variants of an algorithm within an object and be able to switch from one algorithm to another during runtime.
2. Use the Strategy when you have a lot of similar classes that only differ in the way they execute some behavior.
3. Use the pattern to isolate the business logic of a class from the implementation details of algorithms that may not be as important in the context of that logic.
4. Use the pattern when your class has a massive conditional statement that switches between different variants of the same algorithm.

## How to Implement
1. In the context class, identify an algorithm that’s prone to frequent changes. It may also be a massive conditional that selects and executes a variant of the same algorithm at runtime.

2. Declare the strategy interface common to all variants of the algorithm.

3. One by one, extract all algorithms into their own classes. They should all implement the strategy interface.

4. In the context class, add a field for storing a reference to a strategy object. Provide a setter for replacing values of that field. The context should work with the strategy object only via the strategy interface. The context may define an interface which lets the strategy access its data.

5. Clients of the context must associate it with a suitable strategy that matches the way they expect the context to perform its primary job.