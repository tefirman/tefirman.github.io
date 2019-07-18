---
layout: post
title:  "Centennial State<br>Political Geography"
date:   2019-07-18
excerpt: "Let's take a comprehensive look at the divergent political geography of Colorado and its effect on the 2020 Senate race..."
image: "/images/CO_Maps_Wide.png"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="Centennial State Political Geography">
<meta name="twitter:description" content="Let's take a comprehensive look at the divergent political geography of Colorado and its effect on the 2020 Senate race...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/CO_Maps_Wide.png">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">

<script src="/assets/js/jquery.min.js"></script> 
<script> 
$(function(){
  $("#includedContent").load("/images/PrecinctPartisanLeanCO.html"); 
});
</script>
<script> 
$(function(){
  $("#includedContent2").load("/images/PrecinctTrumpEffectCO.html"); 
});
</script>
<script> 
$(function(){
  $("#includedContent3").load("/images/FlippablePrecinctsCO.html"); 
});
</script> 
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-141691742-13"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-141691742-13');
</script>
</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Colorado has been <a href="https://en.wikipedia.org/wiki/Politics_of_Colorado">considered purple since the 90's</a>, but has been <a href="https://www.5280.com/2018/11/colorado-is-still-a-very-purple-state-at-least-for-now/">steadily turning blue in recent years</a>. So why is the <a href="https://fivethirtyeight.com/features/its-early-but-colorados-cory-gardner-has-a-tough-road-to-re-election-in-2020/">upcoming Senate race</a> between incumbent Republican Senator Cory Gardner and his hypothetical Democratic opponent still something the citizenry should pay attention to? For starters, the Senate is an unfair playing field, so we should care about every race. The way Senators are apportioned provides <a href="https://tefirman.github.io/blog/UnequalRepresentation/">disproportionate power to citizens of certain states</a>, even more so than the electoral college, so every seat is important. But perhaps a more interesting reason is that the divergent political geography of the Centennial State makes the potential outcome of this race much foggier. In order to illustrate this, I set out to map the behavior of political partisanship throughout the state of Colorado.

Mapping partisanship by county is actually pretty simple considering that county outlines are readily available from the US Census Bureau. However, different parts of the county take part in different races. For instance, Douglas County votes in both the 4th and 6th congressional districts. Grouping these voters into one statistic would create an apples to oranges comparison in that the 58,000 DougCo voters that voted in the 6th congressional district faced a different choice than the 117,000 that voted in the 4th congressional district. Furthermore, counties can be rather large (Douglas County is 840 mi<sup>2</sup>) so the partisan characteristics of one end of the county could be very different from the other.

On the other hand, individual voting precincts are much smaller in area and all voters in each precinct vote in the same races, providing a fair comparison across the board. However, the actual mapping of these results is rather difficult for multiple reasons. Precincts are drawn by each respective county, so you have to go to each of the 64 county clerk offices to find the outlines of the precincts they preside over. In the easiest cases, GIS shapefiles are readily available for download on their website. In the more difficult cases, hand drawn maps need to be manually converted to shapefiles using <a href="https://automeris.io/WebPlotDigitizer/">WebPlotDigitizer</a> and multiple Python modules. In the worst cases, the county clerk doesn't have an email address and won't return your phone calls. As a result, I wouldn't recommend using the following maps in any sort of official capacity to identify which precinct you vote in, but I do think these maps are pretty unique and comprehensive.

To define the scope of the analysis shown here, let's consider results from presidential and midterm elections in the state of Colorado between 2012 and 2018. As a disclaimer, the metrics I'll be using are similar (if not identical) to <a href="https://fivethirtyeight.com/features/election-update-the-house-districts-that-swing-the-most-and-least-with-the-national-mood/">those used by analysts at FiveThirtyEight</a>. There's no way I'm smart enough to have invented these metrics, just smart enough to know how to apply them. Starting with the basics, <b>partisan lean</b> is a <a href="https://fivethirtyeight.com/features/everything-is-partisan-and-correlated-and-boring/">fairly standard</a> <a href="https://en.wikipedia.org/wiki/Cook_Partisan_Voting_Index">metric</a> of whether an area is more Republican or Democratic, but we will define it explicitly as

$$L_i = \frac{1}{N_i} \sum_{j=1}^{N_i} (D_{i,j} - R_{i,j}).$$

where $$i$$ is the precinct index, $$N_{i}$$ is the number of races in the precinct, $$j$$ is the election index (e.g. 2018 District 3 State House race, 2014 Senate race, etc.), and $$D_{i,j}$$ and $$R_{i,j}$$ are the percentage of Democratic and Republican votes, respectively, for race $$j$$ in precinct $$i$$. The map below illustrates this metric for each precinct throughout the state in the form of a heat map with darker shades of red representing more Republican areas and darker shades of blue representing more Democratic areas. The general trends are not surprising in that more densely populated areas (e.g. Denver, Boulder, Fort Collins) tend to be more Democratic and more sparse rural areas (e.g. the entire eastern third of the state) tend to be more Republican, but seeing where the exact lines are drawn is both interesting and informative.

<div align="center"><div id="includedContent"></div></div><br>

However, these partisan predilections do not remain static over time. Precinct leans can easily change based on both the impact of current events and the changing makeup of voting populations. For instance, the 2018 midterms in Colorado saw an 8.1% increase in voter turnout compared to 2014. Numerous things changed in those four years, but the most obvious and earth-shattering one in terms of politics was the election of our current president. To illustrate its effect on voters' behaviors, we'll use what I'm calling the <b>Trump effect</b>: it calculates the lean of a precinct using only races from the 2018 midterms and subtracts the lean of the same precinct using only the 2014 midterms. This isolates where voters are trending due to the instability and antics of the current resident of the White House. As you can see in the map below, the sea of cerulean is not good news for Cory Gardner, especially considering <a href="https://projects.fivethirtyeight.com/congress-trump-score/cory-gardner/">he votes in line with Trump 90% of the time.</a>

<div align="center"><div id="includedContent2"></div></div><br>

Another interesting and lesser-known metric is <b>partisan elasticity</b>, <a href="https://fivethirtyeight.com/features/election-update-the-house-districts-that-swing-the-most-and-least-with-the-national-mood/">an index of how stubborn voters are with their partisanship</a>, i.e. are they voting party lines down the ballot or will they vote for the other party if the right candidate comes along. This will be defined as the standard deviation of the partisan lean, or using the same variables from the first equation,

$$E_i = \sqrt{\frac{1}{N_i} \sum_{j=1}^{N_i} (D_{i,j} - R_{i,j})^2 - L_i^2}.$$

<a href="/images/PrecinctPartisanElasticityCO.html">In isolation</a>, the relevance of a precinct's elasticity is kind of hard to grasp, but when put in context with its associated lean, elasticity teases out valuable insight for potential candidates. Let's say a campaign wanted to identify areas where a candidate's effort would have the most impact. To do this, we can look at "flippable" precincts, precincts that have elasticities larger than the magnitude of their lean. To get the most bang for our buck, let's also limit the scope to precincts with voter densities higher than 100 per square mile.

<div align="center"><div id="includedContent3"></div></div><br>

Fascinatingly, the map above shows us that the majority of these flippable precincts are in the suburban neighborhoods surrounding the major cities along the Front Range. Keep in mind that winning over precincts is not the goal in a Senate race, winning over voters is, so this metric of flippability should not be the golden standard. In order to get past the primary, a Democrat needs to visit the major cities since that's where the majority of Democrats reside. Even in the general, a smaller elasticity could still swing more votes overall <a href="/images/PrecinctVoterDensityCO.html">if the precinct is dense enough</a>. However, these suburban conditions provide a great opportunity for a candidate to knock on doors, shake a few hands, and have the fabled "kitchen table discussions" with everyday voters. Gaining Democratic support in these neighborhoods would kill two birds with one stone: they vote for you in the primary and persuade their undecided neighbors during the general.

So which candidates might we be seeing in these flippable precincts come March? And which of them should we be paying attention to? If online presence has anything to do with it, <a href="https://www.mikejohnstonforcolorado.com/">former State Senator Mike Johnston</a> should be at the top of the list. Of the declared candidates, Johnston has the highest relative search interest via <a href="https://trends.google.com/trends/?geo=US">Google Trends</a> over the past two years, the most <a href="https://www.facebook.com/MikeJohnstonCO/">Facebook likes</a>, and the third most <a href="https://twitter.com/MikeJohnstonCO">Twitter followers</a> as of June 23, 2019 (see table below). And since <a href="https://www.denverpost.com/2019/04/02/mike-johnston-fundraising-senate-cory-gardner/">money</a> definitely has something to do with primaries, it should be mentioned that Johnston has <a href="https://www.fec.gov/data/elections/senate/CO/2020/">twice the fundraising</a> as the rest of the field combined. Honestly, he should be more worried about individuals who have yet to join the race, e.g. if Hickenlooper decides to stop the exercise in narcissism that is his presidential campaign, or if Perlmutter decides it's time to upgrade from the House of Representatives.

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

<h3>Online Presence and Fundraising of Declared Democratic Senate Candidates</h3>
<table id="myTable">
  <tr height="50">
    <th onclick="sortTable(0)">Candidate</th>
    <th onclick="sortTableNumber(1)">Relative Search Interest</th>
    <th onclick="sortTableNumber(2)">Twitter Followers</th>
    <th onclick="sortTableNumber(3)">Facebook Likes</th>
    <th onclick="sortTableNumber(4)">Fundraising</th>
  </tr>
  <tr height="5">
  <td>Mike Johnston</td>
    <td>369</td>
    <td>14,610</td>
    <td>14,789</td>
    <td>$1,804,923.52</td>
  </tr>
  <tr height="5">
  <td>Andrew Romanoff</td>
    <td>76</td>
    <td>4,509</td>
    <td>7,800</td>
    <td>$504,095.35</td>
  </tr>
  <tr height="5">
  <td>Diana Bray</td>
    <td>0</td>
    <td>195</td>
    <td>527</td>
    <td>$72,514.38</td>
  </tr>
  <tr height="5">
  <td>Trish Zornio</td>
    <td>19</td>
    <td>72,487</td>
    <td>2,983</td>
    <td>$59,048.41</td>
  </tr>
  <tr height="5">
  <td>Lorena Garcia</td>
    <td>53</td>
    <td>808</td>
    <td>1,941</td>
    <td>$14,266.15</td>
  </tr>
  <tr height="5">
  <td>Dustin Leitzel</td>
    <td>0</td>
    <td>420</td>
    <td>415</td>
    <td>$5,603.00</td>
  </tr>
  <tr height="5">
  <td>John Walsh</td>
    <td>181</td>
    <td>7,263</td>
    <td>2,301</td>
    <td>$0.00</td>
  </tr>
  <tr height="5">
  <td>Stephany Rose Spaulding</td>
    <td>66</td>
    <td>3,225</td>
    <td>3,228</td>
    <td>$0.00</td>
  </tr>
  <tr height="5">
  <td>Dan Baer</td>
    <td>29</td>
    <td>15,353</td>
    <td>5,490</td>
    <td>$0.00</td>
  </tr>
  <tr height="5">
  <td>Alice Madden</td>
    <td>10</td>
    <td>1,021</td>
    <td>766</td>
    <td>$0.00</td>
  </tr>
  <tr height="5">
  <td>Ellen Burnes</td>
    <td>0</td>
    <td>62</td>
    <td>128</td>
    <td>$0.00</td>
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

All of these factors aside, I do think Mike Johnston would make an excellent Senator for Colorado. <a href="https://www.youtube.com/watch?v=xlyBfInS7ec">To paraphrase the wise (albeit fictional) Sam Seaborn</a>, education is the silver bullet and <a href="https://www.chalkbeat.org/posts/co/2010/05/12/effectiveness-bill-advances-in-house/">Johnston's record</a> <a href="https://www.denverpost.com/2013/04/29/colorado-governor-signs-bill-for-illegal-immigrants-in-state-tuition/">in that department</a> is <a href="https://www.westword.com/news/colorado-gubernatorial-candidate-mike-johnston-is-trying-to-build-bridges-in-bridge-burning-times-10459600">second to none</a>. I will note that he may want to tread lightly on that subject considering the <a href="https://www.cpr.org/2018/11/07/colorado-amendment-73-tax-increase-for-public-education-has-failed/">recent results of Colorado Amendment 73</a>, which would have increased public education funding via higher income, corporate, and property taxes. In the flippable precincts mentioned above, <a href="/images/PrecinctAmendment73YesPctCO.html">only 44.2% of voters</a> voted in favor of the amendment. I’m not saying don’t tout your education credentials, just don’t rely entirely on that issue, especially if it’s paired with a tax increase.

Regardless of who ends up being the Democratic nominee, Cory Gardner <a href="https://www.denverpost.com/2019/03/14/cory-gardner-endorsement-mistake/">has not acted with Coloradoans' best interests in mind</a>, <a href="https://www.washingtonpost.com/powerpost/thats-the-model-cory-gardner-stands-up-to-president-trump/2018/01/05/b3b9b2b6-f17b-11e7-b3bf-ab90a706e175_story.html?utm_term=.50900054ae3f">despite his best efforts as of late</a>. Senator Gardner has voted <a href="https://www.denverpost.com/2017/07/29/cory-gardner-health-care-obamacare-repeal-vote/">to repeal health coverage for over 400,000 Coloradoans</a>, <a href="https://www.denverpost.com/2019/03/14/cory-gardner-trump-border-wall-immigration/">uphold President Trump's wasteful and xenophobic border wall</a>, <a href="http://www.cpr.org/2016/06/21/4-gun-control-measures-fail-how-colorados-senators-voted/">oppose common-sense gun laws</a>, and <a href="https://itep.org/trumpgopplanco/">provide 60% of the state's tax cuts to the richest 1% of its citizens</a>. A change needs to be made, and if the Democratic candidate can deftly navigate the unique political geography of Colorado, this historically purple state may just turn blue.

<h6>All statistics presented in the maps shown here were calculated using <a href="https://www.sos.state.co.us/pubs/elections/resultsData.html">official election results from the Colorado Secretary of State website</a>. All precinct shapes were collected from each county's Clerk and Recorder. The <a href="https://github.com/tefirman/StatisticalStumbles/tree/master/ElectionResults_CO">relevant data</a> and <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/ElectionResults_CO.py">python code</a> used to calculate them are available on <a href="https://github.com/tefirman">my GitHub page</a> and precinct shapefiles are available on request.


