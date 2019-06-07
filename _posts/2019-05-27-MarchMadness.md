---
layout: post
title:  "Methods to the Madness"
date:   2019-05-27
excerpt: "Because brackets are hard and chalk is for the faint of heart..."
image: "/images/CoinBracket.png"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Methods to the Madness">
<meta name="twitter:description" content="Because brackets are hard and chalk is for the faint of heart...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/CoinBracket.png">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
<script src="/assets/js/jquery.min.js"></script> 
<script> 
$(function(){
  $("#includedContent").load("/images/MarchMadness_PointDistribution.html"); 
});
</script>
<script> 
$(function(){
  $("#includedContent2").load("/images/MarchMadness_RelativePoints.html"); 
});
</script> 
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-141691742-3"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-141691742-3');
</script>
</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

March Madness has come and gone and it was an exciting (albeit fairly chalk-ish) tournament! To get a little skin in the game, many people join <a href="http://fantasy.espn.com/tournament-challenge-bracket/2019/en/story?pageName=tcmen%5Crules">bracket leagues</a> where they pick a winner for each of the sixty-three match-ups in the bracket. A correct pick is worth 10 points in the round of 64, 20 in the round of 32, 40 in the Sweet Sixteen, 80 in the Elite Eight, 160 points in the Final Four, and 320 points in the championship. At the end of the tournament, the bracket with the most points wins. This year would have been my first victory, were it not for the non-existent three-pointer foul by Samir Doughty (thanks for nothing, Wahoos), so I decided to look into the different methodologies of bracket selection to hopefully improve my odds for next year. There are some <a href="https://bleacherreport.com/articles/1573533-10-fun-ways-to-pick-a-march-madness-bracket#slide0">pretty strange techniques</a> out there (my personal favorite is which mascot would win in a fight), but the most logical one I could come up with uses the projections from our friends over at <a href="https://fivethirtyeight.com">FiveThirtyEight</a>:

Let’s say you have no previous experience with college basketball, but you still want to play in order to have something to talk about with coworkers/old high school buddies/random strangers. To get around your lack of experience, you decide to flip a coin to pick who wins each matchup, i.e. heads means the better seed wins, tails means the worse seed wins. However, to make sure you don't pick a 16-seed going all the way to the Final Four, you decide to use the latest innovation in sports-related coinage: a self-biasing coin whose heads/tails probabilities shift based on the <a href="https://projects.fivethirtyeight.com/march-madness-api/2019/fivethirtyeight_ncaa_forecasts.csv">two teams in each matchup</a> and <a href="https://fivethirtyeight.com/features/how-our-march-madness-predictions-work-2/">FiveThirtyEight’s Elo ratings system. For simplicity’s sake, let’s ignore FiveThirtyEight's travel and injury adjustments (partly because they seem to be shrouded in secrecy) as well as the four initial play-in games (because those games are pointless). Let’s also assume we only know the initial team ratings. So as an example, in the first round Gonzaga-FDU matchup (Go Zags), Gonzaga has a rating of 95.02 and Fairleigh Dickinson has a rating of 70.04. This would suggest that the probability of the coin coming up heads (and Gonzaga winning) would be

$$P_{H} = \frac{1}{1 + 10^{30.464*(70.04 - 95.02)/400}} = 98.8\%$$

and the probability of the coin coming up tails (and FDU winning) would be

$$P_{T} = \frac{1}{1 + 10^{30.464*(95.02 - 70.04)/400}} = 1.2\%.$$

For both the men’s and women’s tournaments, how much better does the specially designed self-biasing coin do compared to a plain old unbiased quarter? What about compared to “chalk” where the better seed always wins? To assess how this method would perform, we can apply it to the past three tournaments using a <a href="https://en.wikipedia.org/wiki/Monte_Carlo_method">Monte Carlo simulation</a>. Using the code located <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/MarchMadnessSim.py">here</a>, we can pick <a href="https://github.com/tefirman/StatisticalStumbles/tree/master/MarchMadnessSims">10,000 brackets for each year</a> and see what the distributions of point values look like for each year compared to chalk or an unbiased coin flip, distributions like the ones below!

<div align="center"><div id="includedContent"></div></div>

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

<h3>March Madness Results - Chalk vs. Biased Coin</h3>
<table id="myTable">
  <tr height="50">
    <th onclick="sortTable(0)">Season</th>
    <th onclick="sortTable(1)">Gender</th>
    <th onclick="sortTableNumber(2)">Chalk</th>
    <th onclick="sortTableNumber(3)">Simulation Avg.</th>
    <th onclick="sortTableNumber(4)">Simulation St. Dev.</th>
  </tr>
  <tr height="5">
    <td>Unbiased Coin</td>
    <td></td>
    <td></td>
    <td>314.9</td>
    <td>134.7</td>
  </tr>
  <tr height="5">
    <td>2017</td>
    <td>Men</td>
    <td>820</td>
    <td>680.4</td>
    <td>221.7</td>
  </tr>
  <tr height="5">
    <td>2017</td>
    <td>Women</td>
    <td>940</td>
    <td>930.4</td>
    <td>176.5</td>
  </tr>
  <tr height="5">
    <td>2018</td>
    <td>Men</td>
    <td>810</td>
    <td>662.7</td>
    <td>261.4</td>
  </tr>
  <tr height="5">
    <td>2018</td>
    <td>Women</td>
    <td>1190</td>
    <td>924.7</td>
    <td>174.4</td>
  </tr>
  <tr height="5">
    <td>2019</td>
    <td>Men</td>
    <td>920</td>
    <td>802.8</td>
    <td>248.9</td>
  </tr>
  <tr height="5">
    <td>2019</td>
    <td>Women</td>
    <td>1470</td>
    <td>1218.3</td>
    <td>252.6</td>
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
        if (Number(x.innerHTML) > Number(y.innerHTML)) {
          //if so, mark as a switch and break the loop:
          shouldSwitch= true;
          break;
        }
      } else if (dir == "desc") {
        if (Number(x.innerHTML) < Number(y.innerHTML)) {
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

As you may have already guessed, the unbiased coin flip (blue traces) does not do well at all, producing far fewer points than our technically advanced currency regardless of the season. Even when we compare the biased coin results (solid lines) to chalk results (dashed lines), we can see that, on average, the sophisticated FiveThirtyEight method comes close but also falls short of a chalk bracket. However, where the benefit of this method can be seen is in the width of these distributions. If we normalize the three biased coin distributions relative to the chalk point values for the respective years and average them together, this produces the graph below. Again, for both the men's and women's tournaments, the average ratio is below one, but 24.7% of the men's brackets and 21.8% of the women's brackets earn more points than a chalk bracket. Picking chalk may give you more points on average, but if you want to win in a bracket league of ten people, you have to take risks.

<div align="center"><div id="includedContent2"></div></div>

The real test would be to compare this method's results to the actual brackets that fanatical sports enthusiasts submit, but I'll leave that for next year's analysis. Hopefully this method helps all of us in next year's basketball-related spring psychosis!

<h6>The <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/MarchMadnessSim.py">python code</a> and <a href="https://github.com/tefirman/StatisticalStumbles/tree/master/MarchMadnessSims">simulations</a> used to generate the values and figures above are available on <a href="https://github.com/tefirman">my GitHub page</a>.

