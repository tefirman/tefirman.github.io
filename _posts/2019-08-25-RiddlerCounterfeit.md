---
layout: post
title:  "Riddler Answer:<br>Fool the Bank"
date:   2019-08-25
excerpt: "Put on your Hamburglar costumes, Riddler fans! This week's Riddler takes a foray into racketeering..."
image: "/images/FoolTheBankWidgetPic.jpg"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Riddler Answer: Fool the Bank">
<meta name="twitter:description" content="Put on your Hamburglar costumes, Riddler fans! This week's Riddler takes a foray into racketeering...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/FoolTheBankWidgetPic.jpg">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
<script src="/assets/js/jquery.min.js"></script> 

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-141691742-15"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-141691742-15');
</script>

</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Put on your Hamburglar costumes, Riddler fans! <a href="https://fivethirtyeight.com/features/can-you-fool-the-bank-with-your-counterfeit-bills/">This week's puzzle</a> takes a foray into racketeering by putting us in the shoes of an expert counterfeiter specializing in $100 bills. In one last hurrah, we need to optimize the number of fake bills to deposit alongside $2500 worth of real bills, knowing that the bank will randomly inspect 5% of them (rounded up) and have a 25% chance of detecting fake bill after inspecting it. Let's do this thing...

## Solution

To start, let's define $$a$$ as the portion of bills inspected, $$R$$ as the number of real bills you deposit, and $$F$$ as the number of fake bills you deposit. This would put the number of randomly inspected bills at

$$n = \text{ceil}(a(R + F)).$$

From here, we need to think about the probability (and therefore <a href="https://en.wikipedia.org/wiki/Combinatorics">combinatorics) of how many fake/real bills the bank chose to inspect. If we set $$f$$ as the number of fake bills the bank happens to scrutinize, the number of ways the bank could choose $$f$$ fake bills and $$n$$ bills total can be defined as

$$\Omega(f) = \frac{F!}{f!(F - f)!} \times \frac{R!}{(n - f)!(R - n + f)!}.$$

This would put the total number of inspection combinations at

$$Q = \sum_{f=0}^{n} \Omega(f).$$

Let's also define $$p$$ as the probability of a fake's detection. To calculate the probability of success given that $$f$$ fake bills were analyzed, we can normalize $$\Omega$$ using $$Q$$ and add a factor of $$(1 - p)^{f}$$ to account for the bank teller missing the fakes:

$$P(f) = \frac{\Omega(f)}{Q} (1 - p)^{f}.$$

Finally, we can sum this function over all possible values of $$f$$ and multiply by the cash to be gained to get the expected return of our hypothetical caper:

$$E(R,F) = 100(R + F)\sum_{f=0}^{n} P(f).$$

Using $$a = 0.05$$, $$p = 0.25$$, and $$R = 25$$, we can vary $$F$$ to produce the graph seen below and the maximum expected return for our efforts occurs at $$F = 55$$ with a 47.0% probability of winning $8000, suggesting an expected return of $3756.83. But what if the bank decides to modify their protocols and scrutinize a larger portion of the bills? Or what if their techniques improve and increase their detection probablities? Or what if we come into more real bills to use in our endeavor? Play around with the widget below and see how it changes things! Have fun tinkering, Riddler Nation!

<iframe src="https://riddler-fool-the-bank.herokuapp.com/" height="600" width="100%"></iframe>

<h6>The <a href="https://github.com/tefirman/RiddlerCode/blob/master/Riddler_Aug25_Counterfeits.py">python code</a> used to generate the values and figures above are available on <a href="https://github.com/tefirman">my GitHub page</a>.


