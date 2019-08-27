---
layout: post
title:  "Riddler Answer:<br>Fool the Bank"
date:   2019-08-25
excerpt: "This week's Riddler takes a foray into racketeering..."
image: "/images/mcdonalds-hamburglar.jpg"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Riddler Answer: Fool the Bank">
<meta name="twitter:description" content="This week's Riddler takes a foray into racketeering...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/mcdonalds-hamburglar.jpg">
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

You are an expert counterfeiter, and you specialize in forging one of the most ubiquitous notes in global circulation, the U.S. $100 bill. You’ve been able to fool the authorities with your carefully crafted C-notes for some time, but you’ve learned that new security features will make it impossible for you to continue to avoid detection. As a result, you decide to deposit as many fake notes as you dare before the security features are implemented and then retire from your life of crime. You know from experience that the bank can only spot your fakes 25 percent of the time, and trying to deposit only counterfeit bills would be a ticket to jail. However, if you combine fake and real notes, there’s a chance the bank will accept your money. You have $2,500 in bona fide hundreds, plus a virtually unlimited supply of counterfeits. The bank scrutinizes cash deposits carefully: They randomly select 5 percent of the notes they receive, rounded up to the nearest whole number, for close examination. If they identify any note in a deposit as fake, they will confiscate the entire sum, leaving you only enough time to flee. How many fake notes should you add to the $2,500 in order to maximize the expected value of your bank account? How much free money are you likely to make from your strategy?

## Solution

Let's define $$a$$ as the portion of bills inspected, $$R$$ as the number of real bills you deposit, $$F$$ as the number of fake bills you deposit, $$f$$ as the number of fake bills the bank happens to scrutinize, and $$p$$ as the probability of a fake's detection.

$$n = \text{round}(a(R + F))$$

$$\Omega(f) = \frac{F!}{f!(F - f)!} \times \frac{R!}{(n - f)!(R - n + f)!}$$

$$Q = \sum_{f=0}^{n} \Omega(f)$$

$$P(f) = \frac{\Omega(f)}{Q} (1 - p)^{f}$$

$$E(R,F) = 100(R + F)\sum_{f=0}^{n} P(f)$$

Using $$a = 0.05$$, $$p = 0.25$$, and $$R = 25$$, we can vary $$F$$ to produce the graph to the right and the maximum expected return for our little racket occurs at $$F = 44$$ with a 59.3% probability of winning $6900, suggesting an expected return of $4094.36.

<iframe src="https://riddler-fool-the-bank.herokuapp.com/" height="600" width="100%"></iframe>

<h6>The <a href="https://github.com/tefirman/RiddlerCode/blob/master/Riddler_Aug25_Counterfeits.py">python code</a> used to generate the values and figures above are available on <a href="https://github.com/tefirman">my GitHub page</a>.


