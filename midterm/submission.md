### Submission

**Submissions are different for the midterm, so please read this!**

Please **record** yourself talking through these problems and handwriting the solution on a whiteboard. **There should NOT be cuts in the videos.** This means that you must do each problem in one run-through. Please upload these videos (or one video) to YouTube (unlisted), and submit the links for us to watch in another file (covered below). In the description **of the YouTube video** (and not the submitted file), please add the time stamps for each of the rubric points above. For example, the following could be a valid description. We ask you to do this because YouTube allows us to click on the timestamps to quickly go through videos.

You can record two separate videos for the two problems if you would like. This is up to you.

An example YouTube description would look like the following.

```text
- P1 correct algorithm: 0:24
- P1 runtime + explanation: 2:10
- P1 happy case: 3:01
- P1 edge cases: 3:45
```

**If you do not submit a timestamped description, we will need you to resubmit for 5% off!**

Please remember that these videos do not need to be perfect. You can stumble a few times/repeat yourself maybe/have to start sentences over and you will NOT get points off!

### So what exactly are we submitting?

**We want your runnable code and test data!** This will also make sure that your code is correct because you can test it :)

Please zip up a folder with the following contents:

```
chinchilla.(py/java/c/whatever extension)
dolphin.(py/java/c/whatever extension)
youtube_links.txt
```

You are welcome to use whatever programming language you want for this assignment (as usual), but **you must give us instructions on how to run your file with the test data given at the top of each file**. This can be simple and require slight manual entry. For example, my `chinchilla.py` could look like.

```python
# To run this file, please change the argument of the schedule_movies
# call to moviegoers_good or moviegoers_bad depending on which one you
# would like to test! Then, just run 'python chinchilla.py'.

moviegoers_good = [
  {"name": "Ishaan",
   "movies": ("Spiderman", "The Avengers")},
  
  {"name": "Megan",
   "movies": ("Thor", "Spiderman")},

  {"name": "Georgianna",
   "movies": ("Suicide Squad", "Sherlock Holmes")},

  {"name": "Cameron",
   "movies": ("Spiderman", "Wonder Woman")},

  {"name": "Phong",
   "movies": ("The Social Network", "Sherlock Holmes")}
]

moviegoers_bad = [
  {"name": "Ishaan",
   "movies": ("Spiderman", "The Avengers")},
  
  {"name": "Megan",
   "movies": ("Thor", "The Avengers")},

  {"name": "Ally",
   "movies": ("Thor", "Spiderman")},
]

def schedule_movies(moviegoers):
    # my fancy function does stuff here

print schedule_movies(moviegoers_good)
```

Just so you aren't upset that we are making you do this extra work, here is our reasoning behind assigning it like this.

1. We need to make these harder questions easier to grade for us, beacuse otherwise it would take an extremely long time to comb through everyone's code.
2. There are companies that reach out to you with coding challenges to do it this way. [KPCB Fellows](kpcbfellows.com) requires you to implement a hashtable and then submit instructions on how to run it. If they cannot run your code easily, they will not waste their time and try to figure it out! This is bad news bears for you.

Your `youtube_links.txt` file should look like the following:

```text
Chinchilla: https://www.youtube.com/watch?v=esV8bKn8_Js
Dolphin: https://www.youtube.com/watch?v=GshEzAUVcvQ
```

__Please reach out if you have any questions!__