### Chinchilla Problem
##### Out: 10/7/17 | Due: 10/20/17 @ 2:00 PM
___
### Problem
Suppose you are the manager of the brand new movie theater *The Funky Moviewatchers*, and since you care about your customers, you would like them to be able to see every movie on their to-watch list every weekend. Luckily, you are also a telepath, so you always know exactly how many customers you will have on a given weekend, and which movies they want to see. However, **no customer is willing to watch more than one movie on the same day**. Given `n` customers, where each customer wants to watch exactly **two** movies between Saturday and Sunday (they don't care which movie is shown on which day), is it possible to schedule the movies in such a way that every customer is satisfied? If so, construct such a schedule and return it; if not, return `null`.

You can only play a movie once (either on Saturday or Sunday)!

#### Input
Your input will be given to you as a list of `m` customer objects, with the class definition listed below:

```java
class Customer {
  public String name;
  // movies[0] and movies[1] will have the two movies
  public String[] movies;
}
```

#### Output
Your output should be either a list of two sets (one for Saturday, one for Sunday), or `null`. It does not matter which set is first (you can play a set of movies on Saturday or Sunday). An example list might look like the following:

```
[
  {"Terminator", "Inside Out", "Inception", "Forrest Gump"},
  {"A Beautiful Mind", "Up", "The Dark Knight", "8 Mile", "Straight Outta Compton"}
]
```
**Your solution should run in `O(n + m)` time and `O(n + m)` space, where `n` is the total number of unique movies, and `m` is the number of customers**.

#### Assumptions
- You will not be given an empty list of customers
- The movie names are unique

____

### Examples
Let us call the function that does this `schedule_movies(customers)`. Consider the following examples:

```python
moviegoers = [
  {"name": "Ishaan",
   "movies": ("Spiderman", "The Avengers")},
  
  {"name": Megan",
   "movies": ("Thor", "Spiderman")},

  {"name": "Georgianna",
   "movies": ("Suicide Squad", "Sherlock Holmes")},

  {"name": "Cameron",
   "movies": ("Spiderman", "Wonder Woman")},

  {"name": "Phong",
   "movies": ("The Social Network", "Sherlock Holmes")}
]
```
Calling `schedule_movies(moviegoers)` gives us:
```python
[
  {"Spiderman", "Suicide Squad", "The Social Network"},
  {"Thor", "The Avengers", "Sherlock Holmes"}
]
```
or
```python
[
  {"Thor", "The Avengers", "Sherlock Holmes"},
  {"Spiderman", "Suicide Squad", "The Social Network"}
]
```
Consider the example:
```python
moviegoers = [
  {"name": "Ishaan",
   "movies": ("Spiderman", "The Avengers")},
  
  {"name": Megan",
   "movies": ("Thor", "The Avengers")},

  {"name": "Ally",
   "movies": ("Thor", "Spiderman")},
]
```
Caling `schedule_movies(moviegoers)` should output `null` because Thor and Spiderman have to be on the same day because of Ishaan and Megan, but that would not work for Ally.

___
### Hints
You are definitely going to need to construct a graph here. Take advantage of the fact that movies have unique names. Break this question down into different parts like "create graph", "next step", "run a traversal", "etc." and attack each one. You are going to have to create many different data structures here, and so don't be intimidated when you start doing that!

If you're not sure how to create the graph, think about what we have told you `n` and `m` represent and what the expected runtime should be..

___
### Grading
- Explanation of what you are writing as you are writing it and correctness of algorithm [5 pts.]
- Explanation of `O(n + m)` runtime [5 pts.]
- Algorithms uses `O(n + m)` space [5 pts.]
- Walk-through of first moviegoer sample that returns a schedule [3 pts.]
- Walk-through of second moviegoer sample that returns `null` [2 pts.]
- Submitted code that is runnable and works correctly [5 pts.]

___
### Clarifications
If you have any questions about clarification, please post in Piazza! We want to make sure everyone understands the problem. If you have a question, chances are several other people do as well. We will clarify on Piazza and make corrections to this document.

___
### Submission
Please check the `submission.md` file in the `midterm/` directory of this repository.
