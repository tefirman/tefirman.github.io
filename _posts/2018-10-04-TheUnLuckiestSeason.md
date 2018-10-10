---
layout: post
title:  "The (Un)Luckiest Season of All"
date:   2018-10-04
excerpt: "Depending on which statistics you look at, the Seattle Mariners had either the luckiest or unluckiest season in recent memory... #SchrodingersBaseballTeam"
image: "/images/DiazPuzzled.jpg"
---

<head>
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:creator" content="@tefirman51">
<meta name="twitter:site" content="@tefirman51">
<meta name="twitter:title" content="The (Un)Luckiest Season of All">
<meta name="twitter:description" content="Depending on which statistics you look at, the Seattle Mariners had either the luckiest or unluckiest season in recent memory... #SchrodingersBaseballTeam">
<meta name="twitter:image:src" content="https://tefirman.github.io/images/DiazPuzzled.jpg">
<meta name="twitter:image:width" content="280">
<meta name="twitter:image:height" content="150">
</head>

On September 19th, the Seattle Mariners were 84-68, a record that in any other season would send even the ficklest Seattle fan clamoring for their suddenly fashionable Griffey jerseys gathering dust in the back of their closets. But in this logic-defying year of baseball, their season was effectively over despite being a game or less behind four of the ten available playoff spots. With the A's and Astros streaking into October, what would normally amount to at least a playoff chase was reduced to nothing more than consolation games.

<span class="image right"><img src="{{ "/images/RealVsPythagHeatMap.pdf" | absolute_url }}" alt="" /></span>But before we dive too far into self-pity, Mariners fans should probably be thankful that they even got this far considering the team's performance in terms of runs. The easiest stat to point to is run differential where, despite having won more games than lost, the M's allowed 34 more runs than they scored. But the far more interesting stat is the <a href="https://en.wikipedia.org/wiki/Pythagorean_expectation">Pythagorean Win Expectancy (PWE)</a>. According to this metric, they should be sitting at a .478 win percentage, a season-long difference of 12 games compared to the Mariners' final .549 pace. Obviously, credit has to be given to the Herculean effort of Edwin Diaz and his 57 saves, but a little bit of luck had to have been involved, considering that only nine other teams since the deadball era have ever outperformed their PWE by more. (One notable example of these outperformers is the <a href="https://en.wikipedia.org/wiki/1981_Cincinnati_Reds_season">1981 Reds</a>, who actually got shafted much harder than this year's M's due to a strike-shortened season. Despite having the best overall record in the NL, a midseason strike reset the standings, leaving Ken Griffey Sr. out in the cold.)

<span class="image left"><img src="{{ "/images/PlayoffProbHist.pdf" | absolute_url }}" alt="" /></span> Just to give you an idea of how unlucky/lucky this season has been, a team with 89 wins (as the Mariners ended up with) makes the playoffs about 70% of the time according to a logistic regression run by <a href="https://fivethirtyeight.com/features/the-seattle-mariners-cant-catch-a-postseason-break/">FiveThirtyEight</a>. But a team with just 77 wins (as the M’s PWE projects them to have) makes the playoffs less than 1% of the time. The bottom line is that while we should have a better view of the mythical land of playoff baseball, the fact that we’re within a nautical mile is a miracle in itself.

But that doesn’t take away any of the sting, does it? Why is a franchise that has had notoriously terrible playoff luck in recent years getting clubbed over the head by the baseball gods once again? In 2016, <a href="https://twitter.com/No_Little_Plans">Rob Arthur</a> <a href="https://fivethirtyeight.com/features/the-seattle-mariners-cant-catch-a-postseason-break/">unsurprisingly crowned</a> the Seattle Mariners the “Unluckiest MLB Franchise Since 1998” by comparing the number of actual and expected playoff appearances based on regular season records. If we update this to include the last two seasons, it gets even worse. Based on their records, the Mariners should have been to the playoffs an additional three times in the last two decades, almost twice as many as the nearest franchise. Even if we utilize the PWE instead of the actual win percentage to calculate expected playoff appearances, the M’s remain the unluckiest team by almost an entire playoff berth.

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

<h3>Playoff Karma By MLB Franchise</h3>
<table id="myTable">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable(0)">Franchise</th>
    <th onclick="sortTableNumber(1)">Actual</th>
    <th onclick="sortTableNumber(2)">Expected</th>
    <th onclick="sortTableNumber(3)">Difference</th>
    <th onclick="sortTableNumber(4)">Expected (PWE)</th>
    <th onclick="sortTableNumber(5)">Difference (PWE)</th>
  </tr>
  <tr height="5">
    <td>Seattle Mariners</td>
    <td>2</td>
    <td>5.27</td>
    <td>3.27</td>
    <td>4.91</td>
    <td>2.91</td>
  </tr>
  <tr height="5">
    <td>Boston Red Sox</td>
    <td>12</td>
    <td>13.44</td>
    <td>1.44</td>
    <td>13.35</td>
    <td>1.35</td>
  </tr>
  <tr height="5">
    <td>Tampa Bay Rays</td>
    <td>4</td>
    <td>5.26</td>
    <td>1.26</td>
    <td>4.64</td>
    <td>0.64</td>
  </tr>
  <tr height="5">
    <td>Los Angeles Angels</td>
    <td>7</td>
    <td>8.24</td>
    <td>1.24</td>
    <td>6.05</td>
    <td>-0.95</td>
  </tr>
  <tr height="5">
    <td>San Francisco Giants</td>
    <td>7</td>
    <td>8.06</td>
    <td>1.06</td>
    <td>7.6</td>
    <td>0.6</td>
  </tr>
  <tr height="5">
    <td>Toronto Blue Jays</td>
    <td>2</td>
    <td>2.72</td>
    <td>0.72</td>
    <td>4.02</td>
    <td>2.02</td>
  </tr>
  <tr height="5">
    <td>Chicago White Sox</td>
    <td>3</td>
    <td>3.67</td>
    <td>0.67</td>
    <td>3.38</td>
    <td>0.38</td>
  </tr>
  <tr height="5">
    <td>Cincinnati Reds</td>
    <td>3</td>
    <td>3.56</td>
    <td>0.56</td>
    <td>3.8</td>
    <td>0.8</td>
  </tr>
  <tr height="5">
    <td>Cleveland Indians</td>
    <td>8</td>
    <td>8.53</td>
    <td>0.53</td>
    <td>8.19</td>
    <td>0.19</td>
  </tr>
  <tr height="5">
    <td>Washington Nationals</td>
    <td>4</td>
    <td>4.5</td>
    <td>0.5</td>
    <td>5.73</td>
    <td>1.73</td>
  </tr>
  <tr height="5">
    <td>Oakland Athletics</td>
    <td>9</td>
    <td>9.24</td>
    <td>0.24</td>
    <td>8.82</td>
    <td>-0.18</td>
  </tr>
  <tr height="5">
    <td>New York Mets</td>
    <td>5</td>
    <td>5.21</td>
    <td>0.21</td>
    <td>4.38</td>
    <td>-0.62</td>
  </tr>
  <tr height="5">
    <td>Kansas City Royals</td>
    <td>2</td>
    <td>2.09</td>
    <td>0.09</td>
    <td>1.4</td>
    <td>-0.6</td>
  </tr>
  <tr height="5">
    <td>Miami Marlins</td>
    <td>1</td>
    <td>1.04</td>
    <td>0.04</td>
    <td>0.32</td>
    <td>-0.68</td>
  </tr>
  <tr height="5">
    <td>Milwaukee Brewers</td>
    <td>3</td>
    <td>3.02</td>
    <td>0.02</td>
    <td>2.18</td>
    <td>-0.82</td>
  </tr>
  <tr height="5">
    <td>Detroit Tigers</td>
    <td>5</td>
    <td>4.98</td>
    <td>-0.02</td>
    <td>3.73</td>
    <td>-1.27</td>
  </tr>
  <tr height="5">
    <td>Baltimore Orioles</td>
    <td>3</td>
    <td>2.91</td>
    <td>-0.09</td>
    <td>1.59</td>
    <td>-1.41</td>
  </tr>
  <tr height="5">
    <td>Philadelphia Phillies</td>
    <td>5</td>
    <td>4.86</td>
    <td>-0.14</td>
    <td>5.13</td>
    <td>0.13</td>
  </tr>
  <tr height="5">
    <td>Texas Rangers</td>
    <td>7</td>
    <td>6.8</td>
    <td>-0.2</td>
    <td>4.49</td>
    <td>-2.51</td>
  </tr>
  <tr height="5">
    <td>Pittsburgh Pirates</td>
    <td>3</td>
    <td>2.62</td>
    <td>-0.38</td>
    <td>2.03</td>
    <td>-0.97</td>
  </tr>
  <tr height="5">
    <td>San Diego Padres</td>
    <td>3</td>
    <td>2.5</td>
    <td>-0.5</td>
    <td>2.3</td>
    <td>-0.7</td>
  </tr>
  <tr height="5">
    <td>Arizona Diamondbacks</td>
    <td>6</td>
    <td>5.48</td>
    <td>-0.52</td>
    <td>5.04</td>
    <td>-0.96</td>
  </tr>
  <tr height="5">
    <td>Los Angeles Dodgers</td>
    <td>10</td>
    <td>9.28</td>
    <td>-0.72</td>
    <td>8.24</td>
    <td>-1.76</td>
  </tr>
  <tr height="5">
    <td>New York Yankees</td>
    <td>17</td>
    <td>16.14</td>
    <td>-0.86</td>
    <td>14.26</td>
    <td>-2.74</td>
  </tr>
  <tr height="5">
    <td>Houston Astros</td>
    <td>8</td>
    <td>6.89</td>
    <td>-1.11</td>
    <td>7.83</td>
    <td>-0.17</td>
  </tr>
  <tr height="5">
    <td>Atlanta Braves</td>
    <td>12</td>
    <td>10.83</td>
    <td>-1.17</td>
    <td>11.51</td>
    <td>-0.49</td>
  </tr>
  <tr height="5">
    <td>St. Louis Cardinals</td>
    <td>12</td>
    <td>10.79</td>
    <td>-1.21</td>
    <td>11.34</td>
    <td>-0.66</td>
  </tr>
  <tr height="5">
    <td>Colorado Rockies</td>
    <td>4</td>
    <td>2.71</td>
    <td>-1.29</td>
    <td>2.09</td>
    <td>-1.91</td>
  </tr>
  <tr height="5">
    <td>Chicago Cubs</td>
    <td>8</td>
    <td>6.57</td>
    <td>-1.43</td>
    <td>6.49</td>
    <td>-1.51</td>
  </tr>
  <tr height="5">
    <td>Minnesota Twins</td>
    <td>7</td>
    <td>5.07</td>
    <td>-1.93</td>
    <td>2.86</td>
    <td>-4.14</td>
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
      if (switchcount == 0 && dir == "asc") {
        dir = "desc";
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

So why can’t the M’s catch a break after seventeen long years of frustration? Well, for a couple reasons: (1) <a href="https://en.wikipedia.org/wiki/Gambler%27s_fallacy">That’s not how probability works.</a> Past outcomes do not affect future probabilities. If I flip a coin and get ten heads in a row, the odds of getting heads an eleventh time are still 50-50. A baseball doesn’t remember previous seasons and then adjust its path accordingly. (2) As many of you may have seen by now, the AL has a <a href="https://fivethirtyeight.com/features/the-orioles-and-royals-could-at-least-still-beat-a-triple-a-team-right/">parity (read: tanking) problem</a>, where bad teams appear worse and good teams appear better. The standard deviation of win percentages in the AL is the largest in either league since 1962 and the range is the largest since 1954 (thanks Baltimore). This wide spread means that just being good won’t cut it. Only absurd 97-win seasons will keep you in the running, a feat that was achieved by the second wild card Oakland Athletics.

So to mentally put this season to bed, the 2018 Mariners are either extremely lucky or unlucky based on what statistics you look at. I choose to see it in a positive light as a lucky one, but all of this analysis boils down to the age-old philosophical question of whether your beer is half empty or half full. Regardless, order another one because professional sports’ longest playoff drought is lasting at least another year and the A’s and Astros are playing in October.

<h6>MLB season-by-season data was provided by <a href="https://www.retrosheet.org/gamelogs/index.html">Retrosheets</a> and <a href="https://www.baseball-reference.com/leagues/MLB/2018-standings.shtml">Baseball-Reference</a>, and the Python code used to process this data is available <a href="https://github.com/tefirman/StatisticalStumbles/blob/master/RecordAnalysis.py">here</a> on <a href="https://github.com/tefirman">my Github page</a>.


