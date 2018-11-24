---
layout: post
title:  "When Red Becomes Purple"
date:   2018-11-23
excerpt: "The Colorado 6th Congressional District is a perfect example of why every turf matters..."
image: "/images/DougCoPurple.png"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="When Red Becomes Purple">
<meta name="twitter:description" content="TThe Colorado 6th Congressional District is a perfect example of why every turf matters...">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/DougCoPurple.png">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
</head>

Canvassing in any scenario is uncomfortable. Canvassing for a Democratic candidate in a historically Republican district is panic-attack-inducing. But in any campaign, it's a necessary component. So when my partner and I began volunteering for the Douglas County portion of Jason Crow's congressional campaign in Colorado's 6th district (CO-6), it seemed like a daunting but worthy challenge. Given the chaotic state of our democracy, a little more is required of average Americans. We are called to endure the occasional door slam to find the few individuals who remain undecided, who aren't sure where to vote, who need a little extra motivation to even vote at all. We are called to tolerate the surly "leave me alone"'s to ensure that the voice of every citizen is heard in our society.

These efforts were particularly necessary in the turf that we were assigned to. Before last Tuesday, Douglas County going red was essentially a foregone conclusion. In the <a href="https://www.douglas.co.us/elections/historical-election-data/">three previous House races in this district</a>, Democrats have won exactly zero precincts and lost by an average of more than 26 percentage points. Let that sink in for a second. That means that over six years, not a single neighborhood thought "maybe we should shake things up a bit." With this level of incumbency advantage, we had our work cut out for us, but other indicators left a whiff of possibility in the air. Unprecedented <a href="https://www.opensecrets.org/overview/">individual contribution levels</a> of Democrats across the country (including <a href="https://www.opensecrets.org/races/candidates?cycle=2018&id=CO06&spec=N">this one</a>) provided a significant advantage and could have suggested a grass roots mobilization of previously silent Democrats across the country. Midterm elections are <a href="https://fivethirtyeight.com/features/trumps-approval-rating-is-up-republican-house-chances-are-down-does-that-make-any-sense/">always difficult for the party controlling the White House</a>, and with the <a href="https://projects.fivethirtyeight.com/trump-approval-ratings/?ex_cid=rrpromo">considerable unpopularity of President Trump</a>, the fact that the Republican incumbent Mike Coffman <a href="https://projects.fivethirtyeight.com/congress-trump-score/mike-coffman/">voted with Trump 96% of the time</a> was a major selling point to independent voters. Having a moderate Army Ranger candidate with a progressive stance on gun violence in a region that has been rocked by shootings in recent years didn't hurt either. So when election day rolled around and one of Jason Crow's aides jokingly asked "you gonna win us DougCo?", I understood the sarcasm but confidently replied, "we'll win a few precincts for sure."

<span class="image right"><img src="{{ "/images/DougCoHistory.pdf" | absolute_url }}" alt="" /></span>As results came pouring in, this prediction turned out to be an understatement. Jason Crow went on to take thirteen precincts in Douglas County and only lost the county by six percentage points. Losing in any fashion may not sound like an uplifting fact, but the 22.0% jump from losing by 27.9% in 2016 to only 5.9% in 2018 is the largest gain out of all the counties in the district (Adams: 16.4%, Arapahoe: 19.8%).

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

<h3>Recent House Races in the DougCo Portion of CO-6</h3>
<table id="myTable">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTableNumber(0)">Year</th>
    <th onclick="sortTable(1)">Dem. Candidate</th>
    <th onclick="sortTableNumber(2)">Vote %</th>
    <th onclick="sortTableNumber(3)">Margin of Defeat (%)</th>
    <th onclick="sortTableNumber(4)">Precincts Won</th>
  </tr>
  <tr height="5">
    <td>2012</td>
    <td>Joe Miklosi</td>
    <td>35.4</td>
    <td>24.7</td>
    <td>0</td>
  </tr>
  <tr height="5">
    <td>2014</td>
    <td>Andrew Romanoff</td>
    <td>34.5</td>
    <td>27.5</td>
    <td>0</td>
  </tr>
  <tr height="5">
    <td>2016</td>
    <td>Morgan Carroll</td>
    <td>33.3</td>
    <td>27.9</td>
    <td>0</td>
  </tr>
  <tr height="5">
    <td>2018</td>
    <td>Jason Crow</td>
    <td>45.8</td>
    <td>5.9</td>
    <td>13</td>
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

<span class="image left"><img src="{{ "/images/DougCoDownTheBallot.pdf" | absolute_url }}" alt="" /></span>So what happened to Douglas County voters? Why the sudden purple hue? Races further down the ballot give us some insight into why the citizens of Douglas County voted the way they did, and we see that these results don't quite fit the "blue wave" narrative that everyone is so fond of using. Across the board, Democrats did get a bump compared to previous years because of all the factors listed above, but some of that advantage disappears down the ballot. The higher profile races with national implications, i.e. the House and Governor's races, only had a Republican edge of 5.9% while the race for Attorney General ballooned up to 13.5%. This could suggest that voters wanted to rebuke the White House while keeping local government conservative.

<h3>Races Down the Ballot in the DougCo Portion of CO-6</h3>
<table id="myTable2">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable2(0)">Position</th>
    <th onclick="sortTableNumber2(1)">Republican Vote %</th>
    <th onclick="sortTableNumber2(2)">Democrat Vote %</th>
    <th onclick="sortTableNumber2(3)">Margin (%)</th>
  </tr>
  <tr height="5">
    <td>House</td>
    <td>51.7</td>
    <td>45.8</td>
    <td>5.9</td>
  </tr>
  <tr height="5">
    <td>Governor</td>
    <td>51.6</td>
    <td>45.7</td>
    <td>5.9</td>
  </tr>
  <tr height="5">
    <td>Secretary of State</td>
    <td>53.6</td>
    <td>44.6</td>
    <td>9.0</td>
  </tr>
  <tr height="5">
    <td>State Treasurer</td>
    <td>54.3</td>
    <td>43.8</td>
    <td>10.5</td>
  </tr>
  <tr height="5">
    <td>Attorney General</td>
    <td>55.5</td>
    <td>42.0</td>
    <td>13.5</td>
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

So if the <a href="https://fivethirtyeight.com/features/the-suburbs-all-kinds-of-suburbs-delivered-the-house-to-democrats/">suburbs were what handed Democrats the House in 2018</a>, the Douglas County portion of CO-6 should be exhibit A. Obviously, part of Jason Crow's success in this area was regression to the mean -- it was already so red that there was really nowhere to go but up -- but it even stands out when comparing apples to apples. Out of the the top ten districts most similar to CO-6 according to <a href="https://fivethirtyeight.com/methodology/how-fivethirtyeights-house-and-senate-models-work/">FiveThirtyEight's similarity metrics</a>, three were held by a Republican before the midterms. All three seats flipped to the Democrats, but in terms of gain in vote margin, CO-6 just barely finishes second to Kansas's 3rd district (KS-3) by only 0.3%. In fact, the comparison between Jason Crow's victory and <a href="https://projects.fivethirtyeight.com/2018-midterm-election-forecast/house/kansas/3/">Sharice Davids' victory in KS-3</a> is actually rather fitting. In the primaries, Davids' defeated a Bernie-Sanders-endorsed candidate to move on to the general election, possibly suggesting a desire for moderate candidates in KS-3 similar to CO-6. And while the storyline of a gay Native American MMA-fighter candidate will generate more national attention than yet another white male running for congress, the energy levels behind both campaigns in historically red districts seem reminiscent of each other.

<h3> Demographically, Geographically, and Politically Similar Districts to CO-6</h3>
<table id="myTable3">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable3(0)">District</th>
    <th onclick="sortTableNumber3(1)">2016 Margin of Defeat (%)</th>
    <th onclick="sortTableNumber3(2)">2018 Margin of Victory (%)</th>
    <th onclick="sortTableNumber3(3)">Democratic Gain (%)</th>
  </tr>
  <tr height="5">
    <td>CO-6</td>
    <td>8.3</td>
    <td>11.2</td>
    <td>19.5</td>
  </tr>
  <tr height="5">
    <td>CA-49</td>
    <td>0.5</td>
    <td>7.4</td>
    <td>7.9</td>
  </tr>
  <tr height="5">
    <td>CA-25</td>
    <td>6.3</td>
    <td>6.4</td>
    <td>12.7</td>
  </tr>
  <tr height="5">
    <td>KS-3</td>
    <td>10.7</td>
    <td>9.1</td>
    <td>19.8</td>
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

Two and a half weeks of door-knocking, organizing, and getting out the vote felt far more like two and a half months. It would normally be difficult to imagine how people would have survived the entire campaign, but the energy and passion for change of the volunteers that came to make a difference had to have something to do with it. There's no way you make it through an entire campaign without expert phone-bankers like Connie, without unstoppable doorknockers like Brian and Sam, and without energy boosts from seasoned campaign veterans like my partner, Ashley (of course I was going to shamelessly brag about my wife at some point during this article). Jason Crow and his team ran a hell of a campaign, but if there's anyone to credit with this win, it's the citizens of Colorado's 6th district that gave their time, sweat, and effort to the idea that change can materialize anywhere. More than anything, that is what it takes to turn red into purple.








