---
layout: post
title:  "Riddler Answer: Printers are from Mars, Scanners are from Venus"
date:   2019-01-14
excerpt: "Captain Blondebeard would be so proud..."
image: "/images/Mars.jpg"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Riddler Answer: Printers are from Mars, Scanners are from Venus">
<meta name="twitter:description" content="Captain Blondebeard would be so proud...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/Mars.jpg">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-141691742-5"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-141691742-5');
</script>
</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

This week's <a href="https://fivethirtyeight.com/features/in-space-no-one-can-hear-your-3d-printer-die/">edition</a> of the Riddler from Jerry Myers takes us to our rusty planetary neighbor and asks us to calculate the odds of our survival based on three (fairly unreliable) 3D printers. With Mars being a harsh environment, a vital piece of equipment will break exactly once per day and one of the printers must print a replacement part. However, each printer can only print one piece per day and they each have a 10%, 7.5%, and 5% chance respectively of breaking each day. Based on this less than ideal scenario, what are the odds that you would survive a 1825 day long journey?

## Solution

If I understand the description of the scenario correctly, the only way you would die is if all three printers break in the same day because all other scenarios are fixable. For instance, if printers A and B both fail, printer C can print a part to fix printer B, printer B can then print a piece to fix printer A, and finally, printer A can then print a new part for the vital equipment. By this logic, the probability of surviving the entire journey would be

$$P = (100\% - 10\% * 7.5\% * 5\%)^{1825} = 50.4\%.$$

However, the problem gets much more interesting if we make it a bit more realistic. Specifically, we can make the vital equipment/printer failures a random process using a <a href="https://en.wikipedia.org/wiki/Gillespie_algorithm">Gillespie algorithm</a> like the one shown below. On average, one piece of vital equipment will still break each day and each printer will have the same odds of breaking each day, but there is now a significant chance of having multiple breakages in a single day. When anything breaks, the next available printer will print a replacement but then remain unavailable for the next 24 hours to recharge.

<pre><code>import numpy as np

printerLag = 1.0 # Number of days before a printer is ready to print again
numDays = 1825 # Number of days in your martian adventure
printerRates = np.array([0.05,0.075,0.1]) # Probabilities of each printer breaking
vitalRate = 1.0 # Rate at which vital equipment breaks (measured in malfunctions per day)
numSims = 10000 # Number of simulations to run before averaging

times = []
for numSim in range(numSims):
    if (numSim + 1)%1000 == 0:
        print('Try #' + str(numSim + 1))
    time = 0.0
    printers = np.ones(len(printerRates)) # 1 if operational, 0 if broken
    lastPrint = -1*np.ones(len(printerRates)) # Time of each printer's last print job
    while time < numDays:
        probs = np.append(printerRates*printers,vitalRate)
        overallRate = sum(probs)
        randNum1 = np.random.rand(1)[0]
        time -= np.log(randNum1)/overallRate
        probs = probs/overallRate
        randNum2 = np.random.rand(1)[0]
        while np.any(printers == 0) and np.sum(np.all([printers == 1,time - lastPrint >= printerLag],axis=0)) > 0:
            fixInd = np.where(printers == 0)[0][-1]
            printInd = np.where(np.all([printers == 1,time - lastPrint >= printerLag],axis=0))[0][0]
            printers[fixInd] = 1
            lastPrint[printInd] += 1
            del fixInd
            del printInd
        ind = np.where([randNum2 <= sum(probs[:ind + 1]) for ind in range(len(probs))])[0][0]
        if ind < len(printers):
            printers[ind] = 0
            if np.sum(np.all([printers == 1,time - lastPrint >= printerLag],axis=0)) > 0:
                printInd = np.where(np.all([printers == 1,time - lastPrint >= printerLag],axis=0))[0][0]
                lastPrint[printInd] = time
                printers[ind] = 1
                del printInd
        else:
            if np.any(np.all([printers == 1,time - lastPrint >= printerLag],axis=0)):
                printInd = np.where(np.all([printers == 1,time - lastPrint >= printerLag],axis=0))[0][0]
                lastPrint[printInd] = time
                del printInd
            else:
                break
        del ind
    times.append(time)
del numSim

print('Average Survival Time = ' + str(round(np.average(times),1)) + \
' +/- ' + str(round(np.std(times),1)) + ' days')
print('Probability of Survival = ' + str(round(100*sum(np.array(times) >= numDays)/len(times),1)) + '%')
</code></pre>

<span class="image right"><img src="{{ "/images/SurvivalProb.png" | absolute_url }}" alt="" /><img src="{{ "/images/SurvivalProbability_NumPrinters.png" | absolute_url }}" alt="" /><img src="{{ "/images/SurvivalProbability_PrinterLag.png" | absolute_url }}" alt="" /></span>This added stochasticity changes the entire game. We intrepid Riddler-nauts now have essentially a zero percent chance of surviving our martian journey with an average survival of $$13.2 \pm 12.6$$ days. So what needs to change??? What do our highly-skilled RASA engineers need to focus on to get us to the 1825 day finish line? For starters, let's pretend that the <a href="https://fivethirtyeight.com/features/how-far-would-you-go-to-rig-a-coin-flip/">Riddler Nation Senate</a> decided to approve funding for as many 5% printers as we need to have a 50% chance of survival (man, those senators love their coin flips). If that were the case, we would need seven printers instead of three, as seen in the second figure. But with <a href="http://www.realclearfuture.com/articles/2017/06/01/elon_musk_is_still_the_king_of_low-cost_space_launch_111957.html">space travel costing $1250 per pound at best</a>, each <a href="https://www.homedepot.com/p/Dremel-Digilab-3D45-Advanced-Idea-Builder-3D-Printer-with-Built-In-WiFi-Guided-Leveling-and-RFID-Filament-Recognition-3D45-01/303720938?cm_mmc=Shopping%7CG%7CVF%7CD25T%7C25-9_PORTABLE+POWER%7CDREMEL%7CNA%7CVersa%7c71700000037187511%7c58700004135694341%7c92700034455553438&gclid=EAIaIQobChMIrqDZuYLv3wIVdx-tBh1yhQN-EAQYBCABEgKaqvD_BwE&gclsrc=aw.ds">printer</a> weighing 50 pounds, and each printer costing $1500, the senators are starting to clamor about the extra $256K. Instead, they are encouraging us to optimize the three printers we already have. In the end, lowering the breaking probability of our printers won't help much -- even if the printers never break, it's reasonably probable for more than three pieces of vital machinery to break in a single day and the lag between printing jobs will do us in. Sure enough, simulating this perfect-printer scenario produces an average survival of $$20.5 \pm 20.0$$ days so we should definitely focus on reducing the rate-limiting 24 hour recharging period. In order to reach the 50% goal set by the Senate with our original three printers, we would need to lower the lag time to just under 3 hours as seen in the final figure.

This problem is a perfect example of how deterministic, average-based methods can sometimes be misrepresentative of the real scenario. These simpler methods told us that we had a fighting chance, but let's be honest, malfunctions aren't going to happen like clockwork. Only by accounting for the randomness and noise of the stochastic processes of the real world do we realize that something needs to change or we're going to end up as martian toast. If anyone in Riddler Nation wants to mess around with the simulation or see if a different strategy would be more effective, the underlying code is available <a href="https://github.com/tefirman/RiddlerCode/blob/master/MartianPrinters.py">here</a>. Safe travels, Riddler-nauts!!!


