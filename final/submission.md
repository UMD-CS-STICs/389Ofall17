### Submission

**Submissions are different for the final, so please read this!**

Essay: Please submit a pdf of your response to the essay question. This should be included in the zip file that you upload with your code and video link.

Video: Please record a video of yourself talking through this problems and coding **and running** the solution on HireFlock or Coderpad (we specifically chose these platforms because you can run your code in the environments). **There should NOT be cuts in the videos.** This means that you must do the problem in one run-through. Please upload the video to YouTube (unlisted), and submit the link for us to watch in another file (covered below). In the description **of the YouTube video** (and not the submitted file), please add the timestamps for each of the rubric points above. For example, the following could be a valid description. We ask you to do this because YouTube allows us to click on the timestamps to quickly go through videos.

**NOTE: Just to reiterate, we want to see you run your code in your editor on the examples given so that you know whether your code works!**

An example YouTube description would look like the following.

```text
- Correct algorithm: 0:24
- Runtime + explanation: 2:10
- Happy case: 3:01
- Edge cases: 3:45
```

**If you do not submit a timestamped description, we will need you to resubmit for 5% off!**

Please remember that the video does not need to be perfect. You can stumble a few times/repeat yourself maybe/have to start sentences over and you will NOT get points off!

### So what exactly are we submitting?

**We want your runnable code and test data!** This will also make sure that your code is correct because you can test it :)

Please zip up a folder with the following contents:

```
chinchilla.(py/java/c/whatever extension)
youtube_link.txt
essay.pdf
```

You are welcome to use whatever programming language you want for this assignment (as usual), but **you must give us instructions on how to run your file with the test data given at the top of each file**. This can be simple and require slight manual entry. For example, my `chinchilla.py` could look like.

```python
# To run this file, please change the arguments of the match_DNA
# call to whichever example you would like to test! Then, just
# run 'python chinchilla.py'.

DNA_1 = 'AACG', DNA_2 = 'ATCG'
occlusion_1 = 15, occlusion_2 = 17

DNA_3 = 'ATAC', DNA_4 = 'ATCT'
occlusion_3 = 2, occlusion_4 = 3

def match_DNA(DNA_1, DNA_2, occlusion_1, occlusion_2):
    # function does stuff here

print match_DNA(DNA_1, DNA_2, occlusion_1, occlusion_2)
```

Just so you aren't upset that we are making you do this extra work, here is our reasoning behind assigning it like this.

1. We need to make these harder questions easier to grade for us, beacuse otherwise it would take an extremely long time to comb through everyone's code.
2. There are companies that reach out to you with coding challenges to do it this way. [KPCB Fellows](kpcbfellows.com) requires you to implement a hashtable and then submit instructions on how to run it. If they cannot run your code easily, they will not waste their time and try to figure it out! This is bad news bears for you. Airbnb, Slack, and other companies require you to complete a coding challenge in HackerRank, so if your code is not runnable you will not pass any of the test cases!

Your `youtube_links.txt` file should look like the following:

```text
https://www.youtube.com/watch?v=esV8bKn8_Js
```

__Please reach out if you have any questions!__
