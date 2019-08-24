---
layout: post
title:  "Presidential Vocabulary"
date:   2019-08-24
excerpt: "As we have found out in recent weeks, words absolutely matter, especially coming from a President of the United States..."
image: "/images/PresidentDictionary.jpg"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Presidential Vocabulary">
<meta name="twitter:description" content="As we have found out in recent weeks, words absolutely matter, especially coming from a President of the United States...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/PresidentDictionary.jpg">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-141691742-14"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-141691742-14');
</script>

</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

It seems immensely difficult to form a presidential voice that's strong, reassuring, informative, and fifty other adjectives all at once. Too sophisticated: you're an out-of-touch elitist. Too simple: you're unqualified for the most complex job on the planet. Too soft: you're spineless. Too strong: you're heartless. In an attempt to better characterize presidential vocabularies, I went through every presidential transcript in <a href="https://www.presidency.ucsb.edu/">UC Santa Barbara's American Presidency Project</a> and analyzed the relative frequencies of different words. I recognize that a president's lexical fingerprint extends far beyond just the words they choose, but this will hopefully be a good start.

Because less material available as you go further back in time, we'll focus on presidents with more than 1,000 documents in the database, i.e. Herbert Hoover and onward. Furthermore, we'll exclude functional words like "the", "is", "where", etc. and only consider descriptive lexical words. Let's start with a fun, interactive way of looking at things! Below is an interactive widget comparing the frequencies of different words (y-axis) across different presidents (x-axis). You can type in as many words as you want in the search bar for a side-by-side comparison of those words. You can also break things down by president, by party, or not break them down at all, i.e. frequencies over all presidents combined. Play around with it and see if you can find any interesting comparisons!

<iframe src="https://presidentialvocabs.herokuapp.com" height="600" width="100%"></iframe>

Here are a few interesting examples to check out:

* **"Democrats" vs. "Republicans" broken down by party**: Apparently, politicians are obsessed with whatever party they're not in because Republican presidents are much more likely to mention "democrats" over "republicans" and vice versa for Democratic presidents.
* **Presidential last names broken down by president**: This provides an interesting perspective on which presidents greatly influenced their successors (Roosevelt/Kennedy) and which presidents are the biggest narcissists (Hoover/Trump).
* **"America" vs. "American" vs. "Americans" over all presidents**: I might be reading a bit too far into this one, but it's interesting that presidents tend to emphasize "America" and something being "American" a bit more than actual "Americans". 

I will be the first to point out that the comparisons above don't paint the whole picture. They depend heavily on the exact word you choose to look at and the interpretations largely depend on the observer. To eliminate this subjectivity and get a broader lexical characterization, we can look at statistics that apply across a president's entire vocabulary. One such metric could be the average number of syllables per word for each president, loosely gauging verbal complexity. Along the same lines, we can get a little more sophisticated and measure the <a href="https://en.wikipedia.org/wiki/Entropy_(information_theory)">informational entropy</a> of each president's vocabulary. Explicitly, we will define it as

$$S = - \sum_{i} P_i \log_2 P_i$$

where $$P_i$$ is the probability of a particular word ($$i$$) being said. In a nutshell, this quantity represents how much information is contained in each word on average. If I only use eight unique words equally (corresponding to $$S=3$$), my speech patterns are pretty predictable and I can't be expected to provide any sort of detailed description. But if I use 3500 unique words equally (corresponding to the presidential average of $$S=11.8$$), I can speak with much more precision. The table below contains both statistics for every president since Hoover and an interesting trend emerges: the number of syllables per word gradually decreases with time while informational entropy varies president to president regardless of time. And before anyone jumps to conclusions, if we average over parties instead of presidents, both parties are equal at 2.068 syllables per word and $$S=11.74$$. (By the way, is anyone surprised that Trump is at the bottom of both lists? While we all intuitively knew that 45 wasn't the bright bulb in the box, now we have statistical proof...)

<style>
table {
    border-spacing: 0;
    width: 100%;
    border: 1px solid #ddd;
    line-height: 1
}

th {
    cursor: pointer;
}

th, td {
    text-align: left;
    padding: 0px;
    vertical-align: middle;
    min-height: 1px;
    border-left: 1px solid #ddd;
    border-right: 1px solid #ddd;
}

tr:nth-child(even) {
    background-color: #f2f2f2
}
</style>

<h3>Information Contained in Presidential Vocabularies</h3>
<table id="myTable">
  <tr height="50">
    <th onclick="sortTable(0)">President</th>
    <th onclick="sortTableNumber(1)">Syllables Per Word</th>
    <th onclick="sortTableNumber(2)">Informational Entropy (Bits)</th>
  </tr>
  <tr height="5">
    <td>Barack Obama</td>
    <td>2.04</td>
    <td>11.63</td>
  </tr>
  <tr height="5">
    <td>Donald J. Trump</td>
    <td>1.943</td>
    <td>11.18</td>
  </tr>
  <tr height="5">
    <td>George W. Bush</td>
    <td>2.012</td>
    <td>11.39</td>
  </tr>
  <tr height="5">
    <td>William J. Clinton</td>
    <td>2.013</td>
    <td>11.48</td>
  </tr>
  <tr height="5">
    <td>George Bush</td>
    <td>2.063</td>
    <td>11.7</td>
  </tr>
  <tr height="5">
    <td>Ronald Reagan</td>
    <td>2.081</td>
    <td>11.76</td>
  </tr>
  <tr height="5">
    <td>Jimmy Carter</td>
    <td>2.143</td>
    <td>11.56</td>
  </tr>
  <tr height="5">
    <td>Gerald R. Ford</td>
    <td>2.129</td>
    <td>11.45</td>
  </tr>
  <tr height="5">
    <td>Richard Nixon</td>
    <td>2.158</td>
    <td>11.51</td>
  </tr>
  <tr height="5">
    <td>Lyndon B. Johnson</td>
    <td>2.073</td>
    <td>11.61</td>
  </tr>
  <tr height="5">
    <td>John F. Kennedy</td>
    <td>2.207</td>
    <td>11.49</td>
  </tr>
  <tr height="5">
    <td>Dwight D. Eisenhower</td>
    <td>2.208</td>
    <td>11.53</td>
  </tr>
  <tr height="5">
    <td>Harry S. Truman</td>
    <td>2.16</td>
    <td>11.43</td>
  </tr>
  <tr height="5">
    <td>Franklin D. Roosevelt</td>
    <td>2.146</td>
    <td>11.61</td>
  </tr>
  <tr height="5">
    <td>Herbert Hoover</td>
    <td>2.237</td>
    <td>11.53</td>
  </tr>
</table>

<script>
function sortTable(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable");
  switching = true;
  //Set the sorting direction to ascending:
  dir = "desc"; 
  /*Make a loop that will continue until
  no switching has been done:*/
  while (switching) {
    //start by saying: no switching is done:
    switching = false;
    rows = table.rows;
    /*Loop through all table rows (except the
    first, which contains table headers):*/
    for (i = 1; i < (rows.length - 1); i++) {
      //start by saying there should be no switching:
      shouldSwitch = false;
      /*Get the two elements you want to compare,
      one from current row and one from the next:*/
      x = rows[i].getElementsByTagName("TD")[n];
      y = rows[i + 1].getElementsByTagName("TD")[n];
      /*check if the two rows should switch place,
      based on the direction, asc or desc:*/
      if (dir == "asc") {
        if (x.innerHTML.toLowerCase() > y.innerHTML.toLowerCase()) {
          //if so, mark as a switch and break the loop:
          shouldSwitch= true;
          break;
        }
      } else if (dir == "desc") {
        if (x.innerHTML.toLowerCase() < y.innerHTML.toLowerCase()) {
          //if so, mark as a switch and break the loop:
          shouldSwitch = true;
          break;
        }
      }
    }
    if (shouldSwitch) {
      /*If a switch has been marked, make the switch
      and mark that a switch has been done:*/
      rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
      switching = true;
      //Each time a switch is done, increase this count by 1:
      switchcount ++;      
    } else {
      /*If no switching has been done AND the direction is "asc",
      set the direction to "desc" and run the while loop again.*/
      if (switchcount == 0 && dir == "desc") {
        dir = "asc";
        switching = true;
      }
    }
  }
}

function sortTableNumber(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable");
  switching = true;
  //Set the sorting direction to ascending:
  dir = "desc"; 
  /*Make a loop that will continue until
  no switching has been done:*/
  while (switching) {
    //start by saying: no switching is done:
    switching = false;
    rows = table.rows;
    /*Loop through all table rows (except the
    first, which contains table headers):*/
    for (i = 1; i < (rows.length - 1); i++) {
      //start by saying there should be no switching:
      shouldSwitch = false;
      /*Get the two elements you want to compare,
      one from current row and one from the next:*/
      x = rows[i].getElementsByTagName("TD")[n];
      y = rows[i + 1].getElementsByTagName("TD")[n];
      /*check if the two rows should switch place,
      based on the direction, asc or desc:*/
      if (dir == "asc") {
        if (Number(x.innerHTML.replace(/,/g, '').replace(/\$/g, '')) > Number(y.innerHTML.replace(/,/g, '').replace(/\$/g, ''))) {
          //if so, mark as a switch and break the loop:
          shouldSwitch= true;
          break;
        }
      } else if (dir == "desc") {
        if (Number(x.innerHTML.replace(/,/g, '').replace(/\$/g, '')) < Number(y.innerHTML.replace(/,/g, '').replace(/\$/g, ''))) {
          //if so, mark as a switch and break the loop:
          shouldSwitch = true;
          break;
        }
      }
    }
    if (shouldSwitch) {
      /*If a switch has been marked, make the switch
      and mark that a switch has been done:*/
      rows[i].parentNode.insertBefore(rows[i + 1], rows[i]);
      switching = true;
      //Each time a switch is done, increase this count by 1:
      switchcount ++;      
    } else {
      /*If no switching has been done AND the direction is "asc",
      set the direction to "desc" and run the while loop again.*/
      if (switchcount == 0 && dir == "desc") {
        dir = "asc";
        switching = true;
      }
    }
  }
}
</script>

A few questions naturally follow: How much does the <a href="https://books.google.com/ngrams">language of each president's era</a> increase/decrease their informational entropy? What about the relative frequencies of two-word combinations? Can we categorize the major themes of each president using <a href="https://www.analyticsvidhya.com/blog/2018/04/a-comprehensive-guide-to-understand-and-implement-text-classification-in-python/">text classification?</a> These are all ideas that are in the works and will come soon in a sequel to this post. As we have seen in recent weeks, words absolutely matter, especially those coming from a President of the United States. They can <a href="https://www.youtube.com/watch?v=ueMNqdB1QIE">lift the hopes</a> or <a href="https://www.washingtonpost.com/">stoke the fears</a> of the citizens who hear them. We should all keep track of them in any way we can.

<h6>All statistics presented here are based on documents curated by the <a href="https://www.presidency.ucsb.edu/">American Presidency Project of UC Santa Barbara</a>. <a href="https://github.com/tefirman/PresidentialVocab_App">Detailed datasets and the python code</a> used to generate them are available on <a href="https://github.com/tefirman">my GitHub page</a>.




