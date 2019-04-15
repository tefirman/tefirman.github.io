---
layout: post
title:  "Uneven Democracy"
date:   2019-02-22
excerpt: "Based on how the American government was designed, not all votes are created equal..."
image: "/images/TippedScales.png"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Uneven Democracy">
<meta name="twitter:description" content="Not all votes are created equal...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/TippedScales.png">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
<script src="/assets/js/jquery.min.js"></script> 
<script> 
$(function(){
  $("#includedContent").load("/images/HouseSenateResultsByYear.html"); 
});
</script> 
<script> 
$(function(){
  $("#includedContent2").load("/images/HouseSenateResultsByYear_Alternates.html"); 
});
</script> 
<script> 
$(function(){
  $("#includedContent3").load("/images/TotalPowerMap_Large.html"); 
});
</script> 
</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Americans pride themselves on their democracy, on the idea that everyone has an equal voice in our government, and to be honest, I'm pretty proud of it too (less so in recent years). But if anyone tells you that every citizen truly has an <i>equal</i> voice in our system, they possess one of two things: 1. a misunderstanding of how our government is designed and operated, or 2. a loose definition of the term "equal". In an ideal scenario, each person's voice would be equally valued and political representation on a macroscopic level would be proportional to the views of the American public. As a simple example, a group of 1800 Democrats and 1200 Republicans could be represented by 9 Democrats and 6 Republicans, giving each voter a representative power of 1/200 or 0.005. But let's say that a neighboring group of 900 Republicans and 600 Democrats was represented by 9 Republicans and 6 Democrats. Locally, this is proportional and fair, but macroscopically, we now have equal representation (15-15) for unequal populations (2400-2100) because the second group has twice the representative power (1/100 or 0.01). 

This may seem like an unrealistic example, but this is basically how the United States Senate has operated since 1789 thanks to the <a href="https://en.wikipedia.org/wiki/Connecticut_Compromise">Connecticut Compromise</a>. Gerrymandering has led to similar (but less extreme) situations in the House of Representatives. To illustrate this, we can calculate the representative power of each state or congressional district by dividing the number of representatives/senators they have by the number of voters who participated. Just to clarify units, we will define a 1 representative to 1 voter ratio as a "rep" which would make 1 representative to 1,000,000 voters a "microrep" or &mu;rep. Furthermore, since there are 435 representatives in the House and 100 in the Senate, we will define "Total Power" as 4.35*(Senate Power) + (House Power). The figures shown here illustrate darker colors as higher representative powers, but if you would like to check out the exact values for each state and district, check them out <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/ElectionResults/OverallResults_ByYearAndState.csv">here</a> and <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/ElectionResults/OverallResults_ByYearAndDistrict.csv">here</a>.

<div align="center"><div id="includedContent3"></div></div><br>
<!-- <span class="image fit"><img src="{{ "/images/PowerMapsFigure.png" | absolute_url }}" alt="" /></span> -->
<!-- <a onclick="alert('Hello world!')" class="button special">Special</a> -->

Taking a look at the two extremes, we can see a pretty shocking disparity in representation. A voter in Wyoming has more representative power than a Floridian, a Pennsylvanian, a New Yorker, and a Californian <i>combined</i>. This is purely due to the fact that while each of these five states are represented by two senators, only 400,000 voters pick those two people in Wyoming while over 10,000,000 pick them in each of the other four states. Using state-by-state voter demographics, we can expand the scope of our power metric to compare the average representative power of different demographics to see if any group in particular benefits from this arrangement. Comparisons based on sex and age show fairly similar representation between different groups, but race, political affiliation, and urban/rural delineation produce very unbalanced playing fields. As seen in the tables below, white voters have about 10% more representative power than non-white voters, Republican voters have 28% more than Democratic voters, and rural voters (based on <a href="https://github.com/theatlantic/citylab-data/blob/master/citylab-congress/citylab_cdi.csv">CityLab's classification</a>) have 40% more than urban voters. This is again due to the disparate proportioning of representatives in the Senate and highlights the inherent representative inequity in our country's democracy.

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

<h3>Representative Power By Race in 2016 (microreps)</h3>
<table id="myTable2">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable2(0)">Race</th>
    <th onclick="sortTableNumber2(1)">House Power</th>
    <th onclick="sortTableNumber2(2)">Senate Power</th>
    <th onclick="sortTableNumber2(3)">Total Power</th>
  </tr>
  <tr height="5">
    <td>White</td>
    <td>3.36</td>
    <td>0.79</td>
    <td>6.79</td>
  </tr>
  <tr height="5">
    <td>Black</td>
    <td>3.40</td>
    <td>0.65</td>
    <td>6.25</td>
  </tr>
  <tr height="5">
    <td>Asian</td>
    <td>3.63</td>
    <td>0.62</td>
    <td>6.32</td>
  </tr>
  <tr height="5">
    <td>Hispanic</td>
    <td>3.61</td>
    <td>0.49</td>
    <td>5.76</td>
  </tr>
</table>

<script>
function sortTable2(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable2");
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

function sortTableNumber2(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable2");
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

<h3> Representative Power By Political Party in 2016 (microreps)</h3>
<table id="myTable3">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable3(0)">Party</th>
    <th onclick="sortTableNumber3(1)">House Power</th>
    <th onclick="sortTableNumber3(2)">Senate Power</th>
    <th onclick="sortTableNumber3(3)">Total Power</th>
  </tr>
  <tr height="5">
    <td>Republican</td>
    <td>3.85</td>
    <td>1.00</td>
    <td>8.19</td>
  </tr>
  <tr height="5">
    <td>Democratic</td>
    <td>3.16</td>
    <td>0.74</td>
    <td>6.39</td>
  </tr>
  <tr height="5">
    <td>Other</td>
    <td>0.00</td>
    <td>0.43</td>
    <td>1.88</td>
  </tr>
</table>

<script>
function sortTable3(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable3");
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

function sortTableNumber3(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable3");
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

<h3> Representative Power By Urban, Suburban, and Rural Classification in 2016 (microreps)</h3>
<table id="myTable4">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable4(0)">Party</th>
    <th onclick="sortTableNumber4(1)">House Power</th>
    <th onclick="sortTableNumber4(2)">Senate Power</th>
    <th onclick="sortTableNumber4(3)">Total Power</th>
  </tr>
  <tr height="5">
    <td>Rural</td>
    <td>3.29</td>
    <td>1.17</td>
    <td>8.39</td>
  </tr>
  <tr height="5">
    <td>Suburban</td>
    <td>3.26</td>
    <td>0.69</td>
    <td>6.25</td>
  </tr>
  <tr height="5">
    <td>Urban</td>
    <td>3.90</td>
    <td>0.48</td>
    <td>5.97</td>
  </tr>
</table>

<script>
function sortTable4(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable4");
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

function sortTableNumber4(n) {
  var table, rows, switching, i, x, y, shouldSwitch, dir, switchcount = 0;
  table = document.getElementById("myTable4");
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

On a macroscopic scale, this leads to representation that is disproportionate to the actual populations they represent. Look at the percentages of elected congressional representatives in each party compared to the number of voters who actually voted for that party shown in the first figure below. Wins and votes in the House of Representatives have generally been proportional because the number of representatives is allocated based on population -- until 2010 that is when congressional districts were conveniently redrawn by state governments. Can we talk about 2012 please? Democrats received more votes in aggregate during that election and only received 45% of the delegates. The equivalent graph applied to the Senate is even worse. For each year, we can add up the vote totals for each senator's most recent election (e.g. for 2016, a senator elected in 2014 would contribute their 2014 vote totals) and again compare votes by party to wins by party. As you can see in the second figure, the relationship between these two values is loose at best. Since 2004, the percentage of votes cast for Republican candidates has never exceeded that of Democratic candidates, and yet, four of the seven congresses have had as many or more Republican Senators as Democratic Senators. That doesn't exactly seem fair to me...

<div id="includedContent"></div>

So what does this imbalance of representative power lead to? Unpopular ideas becoming law and popular ideas getting ignored. Despite being <a href="https://www.washingtonpost.com/news/the-fix/wp/2017/07/28/republicans-obamacare-repeal-was-never-really-that-popular/?utm_term=.3e02025c1297">very unpopular amongst the general public</a>, the attempted "skinny repeal" of Obamacare in 2017 almost passed in the Senate with votes from Senators representing only 39.8% of American voters, and it would have, were it not for the dramatic thumbs down of the late Senator John McCain. What did become law was the 2017 Tax Cuts and Jobs Act, <a href="https://news.gallup.com/poll/243611/disapprove-approve-2017-tax-cuts.aspx">another unpopular bill</a> which only needed the votes from Senators representing 40.2% of the electorate. The Supreme Court confirmations of both Neil Gorsuch and Brett Kavanaugh were pushed through by Senators elected by less than 42% of the electorate. Even ignoring actual politics, it's counterintuitive that such a diverse country would elect congress after congress of old white dudes rather than the melting pot that America so eagerly describes itself as.

So why does this happen and what can we do to fix it? <a href="http://www.pewresearch.org/fact-tank/2018/05/21/u-s-voter-turnout-trails-most-developed-countries/">Low voter turnout</a> is a big factor that tends to benefit conservative candidates, which possibly explains why Republicans have received disproportionately higher representation since 2010. The 2018 midterms did show a <a href="https://fivethirtyeight.com/features/the-2018-midterms-in-4-charts/">huge surge in turnout</a> but I can't help but wonder if this is purely a reaction to outrage against President Trump that will quickly fade in future elections. <a href="https://www.pbs.org/newshour/politics/georgia-election-fight-shows-that-black-voter-suppression-a-southern-tradition-still-flourishes">Voter suppression</a> continues to rear its ugly head, though often masquerading as concerns for <a href="https://www.theatlantic.com/politics/archive/2018/11/how-voter-suppression-actually-works/575035/">"voter fraud"</a>. Encouraging those around us to get involved in democracy and protecting the voting rights of every American citizen will help to align the voices of power with the voice of the people. But the more data-centric problem I want to address is gerrymandering and the restructuring of Congress. The exact geometry of congressional districts is a very complicated issue, so I won't get into that level of detail here (though a future post might), but there might be a simpler solution. For those of you who think I'm trying to rewrite the Constitution, take a chill pill, this is just a thought experiment.

Let's imagine a scenario where no districts are drawn. In this scenario, everyone still gets two Senators and the same amount of representatives in the House as before, but rather than voting in individual races, each person votes for a particular party (obviously this is problematic since people's views don't always align with any single party, but bear with me). Representatives and Senators are then divvied out to each party relative to the votes for each party. As you can see in the first two figures below, this setup compensates for most of the mismatch between votes and representation in the House, but the Senate remains inequitable. At least now the number of Senators for each party is proportional to the vote share, but Republican votes still go much further than Democratic ones. In fact, after trying a few different iterations of this model, the only version that produces a Senate that somewhat accurately represents the votes of the people (as seen in the third figure below) is when Senators are reapportioned based on census populations, the number of Senators is increased to 150, and people again vote for a party instead of a candidate. Crazy how far you need to go just to produce a level playing field...

<div id="includedContent2"></div>

I realize that the founding fathers established our government this way for a reason, that the Connecticut Compromise was necessary to get smaller states to ratify the Constitution, and that, like the Electoral College, it helps to guard against the <a href="https://en.wikipedia.org/wiki/Tyranny_of_the_majority">tyranny of the majority</a>. But right now, it feels a hell of a lot like we're at risk of the opposite. A congressional majority elected by a minority of Americans is enabling an unpopular president (also elected by a minority of Americans) to enact legislation opposed by a majority of Americans. The framers were very intentional in their preambular word choice of forming a <i>more perfect</i> union, implying a good start but plenty of room to improve. Maybe it's time to start thinking about making Congress a bit more perfect in terms of representation.

<h6>All statistics presented here were calculated using <a href="https://transition.fec.gov/pubrec/electionresults.shtml">official election results from the FEC</a>. The <a href="https://github.com/tefirman/StatisticalStumbles/tree/master/ElectionResults">relevant data</a> and <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/ElectionResults.py">python code</a> used to calculate them are available on <a href="https://github.com/tefirman">my GitHub page</a>.








