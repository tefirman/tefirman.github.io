---
layout: post
title:  "Riddler Submission"
date:   2018-09-15
excerpt: "Got a riddle published in the Riddler: Life goal complete! Try your hand at a game I call 'Rock-Paper-Scissors-Hop'..."
image: "/images/RockPaperScissorsHop.gif"
---

As you will come to notice throughout the course of this blog, I am a big fan of the website <a href="https://fivethirtyeight.com">FiveThirtyEight</a> and one weekly segment called <a href="https://fivethirtyeight.com/tag/the-riddler/">The Riddler</a> edited by <a href="https://twitter.com/ollie">Oliver Roeder</a>. Every Friday, it challenges its readers to two math/probability/logic puzzles, one shorter, more accessible problem and one longer, more time-consuming problem for the hardcore puzzle nerds. It's a fun way to end the week while stretching your brain and maybe picking up a computational tool or two while you're at it.

After getting hooked and submitting answers for a few months, I started itching to submit a <i>question</i> for the Riddler community. It took a little while, but a problem worthy of this esteemed group came to me a couple of weeks ago, and much to my surprise, it was actually <a href="https://fivethirtyeight.com/features/how-many-hoops-will-kids-jump-through-to-play-rock-paper-scissors/">published!</a> At the time, the following video of a unique schoolyard game had been making the rounds on Facebook and it seemed like a fun thing to model:

<div align="center"><iframe width="560" height="315" src="https://www.youtube.com/embed/PcIord7RNAI" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe></div>

<p></p>
## Idealized Rules of Rock-Paper-Scissors-Hop

<ul>
	<li>Kids stand at either end of N hoops.</li>
	<li>At the start of the game (t = 0), one kid from each end starts hopping at a speed of v = 1 hoop per second until they run into each other, either in adjacent hoops or if they land in the same hoop.</li>
	<li>At that point, they play rock-paper-scissors at a rate of 1 game per second until one of the kids wins.</li>
	<li>The loser goes back to their end of the hoops, a new kid steps up at that end, and the winner and the new player hop until they run into each other.</li>
	<li>This process continues until someone reaches the opposing end and that player wins!</li>
</ul>

Now, imagine you are a gym teacher having a bad day and you want to make sure the kids stay occupied for the entire class. If I put down 8 hoops, how long on average will the game last? How many hoops should I put down if I want the game to last for the entire 30 minute period on average?

## Solution

Obviously, I had to have a solution in order to submit the problem (and I'll get into that in a second), but I was flabbergasted at the kinds of the <a href="https://fivethirtyeight.com/features/the-new-national-pastime-competitive-coin-flipping/">solutions</a> that were submitted. Multiple solvers had code that was <a href="https://github.com/zsegel/538riddler/blob/master/riddler_RPS_hop.py">far</a> <a href="https://gist.github.com/mrichards42/7c63d2ea209081f75dedfaaa08f87e86">more</a> <a href="https://github.com/Saehry/Riddler/blob/master/2018-08-24.py">elegant</a> than mine and the analytical solutions from <a href="https://laurentlessard.com/bookproofs/hoop-hop-showdown/">Laurent Lessard</a> and <a href="http://math.uchicago.edu/~timblack/blog/hoops.html">Tim Black</a> (which cleverly involved a hyper-intelligent firefly) were mind-blowing. So please be warned ahead of time that my solution is not as pretty as those ones, but it still works... #AforEffort #YesIKnowHashtagsDontWorkInBlogs <a href="https://twitter.com/search?q=%23OrDoThey&src=typd">#OrDoThey</a>

The easiest solution is definitely a <a href="https://en.wikipedia.org/wiki/Monte_Carlo_method">Monte Carlo</a> simulation. My coding language of choice is Python, but this can easily been done using pretty much any language: 

<pre><code>import numpy as np

numHoops = 8
leftWinProb = 1.0/3.0
rightWinProb = 1.0/3.0
hopTime = 1
rpsTime = 1

timeVals = []
for numTry in range(1000000):
	if (numTry + 1)%1000 == 0:
		print('Try #' + str(numTry + 1))
	timeVals.append(hopTime)
	leftPos = 0
	rightPos = numHoops - 1
	while rightPos - leftPos > 1:
		timeVals[-1] += hopTime
		leftPos += 1
		rightPos -= 1
	while leftPos < numHoops and rightPos >= 0:
		timeVals[-1] += rpsTime
		rockPaperScissors = np.random.rand()
		while rockPaperScissors >= leftWinProb + rightWinProb:
			timeVals[-1] += rpsTime
			rockPaperScissors = np.random.rand()
		timeVals[-1] += hopTime
		if rockPaperScissors < leftWinProb:
			leftPos += 1
			rightPos = numHoops - 1
		elif rockPaperScissors < leftWinProb + rightWinProb:
			leftPos = 0
			rightPos -= 1
		while np.all([rightPos - leftPos > 1,leftPos < numHoops,rightPos >= 0]):
			timeVals[-1] += hopTime
			leftPos += 1
			rightPos -= 1
del numTry
</code></pre>

I also made an <a href="https://github.com/tefirman/RiddlerCode/blob/master/RockPaperScissorsHop.py">analytical solution</a> that calculates the time and probability of every possible path of a game and it works, but it's a bit overkill and definitely impractical for larger hoop numbers. I honestly think the most original part of my code is the segment that generates a sample gif of a single game to demonstrate how the dynamics work. Despite my answer's lack of elegance, I'm ultimately proud of coming up with the question and inspired by everyone's answers. Thanks for tuning in, gang!


