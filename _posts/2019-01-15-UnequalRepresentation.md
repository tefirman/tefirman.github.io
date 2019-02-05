---
layout: post
title:  "Uneven Democracy"
date:   2019-02-04
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
</head>

<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>

Americans pride themselves on their democracy, on the idea that everyone has an equal voice in our government, and to be honest, I'm pretty proud of it too (less so in recent years). But if anyone tells you that every citizen truly has an <i>equal</i> voice in our system, they possess one of two things: 1. a misunderstanding of how our government is designed and operated, or 2. a loose definition of the term "equal". In an ideal scenario, each person's voice would be equally valued and political representation on a macroscopic level would be proportional to the views of the American public. As a simple example, a group of 1800 Democrats and 1200 Republicans could be represented by 9 Democrats and 6 Republicans, giving each voter a representative power of 1/200 or 0.005. But let's say that a neighboring group of 900 Republicans and 600 Democrats was represented by 9 Republicans and 6 Democrats. Locally, this is proportional and fair, but macroscopically, we now have equal representation (15-15) for unequal populations (2400-2100) because the second group has twice the representative power (1/100 or 0.01). 

This may seem like an unrealistic example, but this is basically how the United States Senate has operated since 1789 thanks to the <a href="https://en.wikipedia.org/wiki/Connecticut_Compromise">Connecticut Compromise</a> and gerrymandering has led to similar (but less extreme) situations in the House of Representatives. To illustrate this, we can calculate the representative power of each state or congressional district by dividing the number of representatives/senators they have by the number of voters who participated. Just to clarify units, we will define a 1 representative to 1 voter ratio as a "rep" which would make 1 representative to 1,000,000 voters a "microrep" or &mu;rep. Also, since there are 435 representatives in the House and 100 in the Senate, we will define "Total Power" as 4.35*(Senate Power) + (House Power).

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

<h3>Representative Power By State in 2016 (microreps)</h3>
<table id="myTable">
  <tr height="50">
   <!--When a header is clicked, run the sortTable function, with a parameter, 0 for sorting by names, 1 for sorting by country:-->  
    <th onclick="sortTable(0)">State</th>
    <th onclick="sortTableNumber(1)">House Power</th>
    <th onclick="sortTableNumber(2)">Senate Power</th>
    <th onclick="sortTableNumber(3)">Total Power</th>
  </tr>
<tr height="5">
  <td>Alabama</td>
  <td>3.7</td>
  <td>1.38</td>
  <td>9.7</td>
</tr>
<tr height="5">
  <td>Alaska</td>
  <td>3.24</td>
  <td>6.74</td>
  <td>32.5</td>
</tr>
<tr height="5">
  <td>Arizona</td>
  <td>3.73</td>
  <td>0.84</td>
  <td>7.4</td>
</tr>
<tr height="5">
  <td>Arkansas</td>
  <td>3.74</td>
  <td>2.05</td>
  <td>12.6</td>
</tr>
<tr height="5">
  <td>California</td>
  <td>3.95</td>
  <td>0.16</td>
  <td>4.7</td>
</tr>
<tr height="5">
  <td>Colorado</td>
  <td>2.59</td>
  <td>0.84</td>
  <td>6.2</td>
</tr>
<tr height="5">
  <td>Connecticut</td>
  <td>3.17</td>
  <td>1.29</td>
  <td>8.8</td>
</tr>
<tr height="5">
  <td>Delaware</td>
  <td>2.38</td>
  <td>6.31</td>
  <td>29.8</td>
</tr>
<tr height="5">
  <td>Florida</td>
  <td>3.06</td>
  <td>0.23</td>
  <td>4.0</td>
</tr>
<tr height="5">
  <td>Georgia</td>
  <td>3.71</td>
  <td>0.62</td>
  <td>6.4</td>
</tr>
<tr height="5">
  <td>Hawaii</td>
  <td>4.84</td>
  <td>3.33</td>
  <td>19.3</td>
</tr>
<tr height="5">
  <td>Idaho</td>
  <td>2.93</td>
  <td>3.58</td>
  <td>18.5</td>
</tr>
<tr height="5">
  <td>Illinois</td>
  <td>3.43</td>
  <td>0.44</td>
  <td>5.3</td>
</tr>
<tr height="5">
  <td>Indiana</td>
  <td>3.39</td>
  <td>0.76</td>
  <td>6.7</td>
</tr>
<tr height="5">
  <td>Iowa</td>
  <td>2.64</td>
  <td>1.5</td>
  <td>9.2</td>
</tr>
<tr height="5">
  <td>Kansas</td>
  <td>3.41</td>
  <td>1.96</td>
  <td>11.9</td>
</tr>
<tr height="5">
  <td>Kentucky</td>
  <td>3.4</td>
  <td>1.2</td>
  <td>8.6</td>
</tr>
<tr height="5">
  <td>Louisiana</td>
  <td>3.33</td>
  <td>1.17</td>
  <td>8.4</td>
</tr>
<tr height="5">
  <td>Maine</td>
  <td>2.69</td>
  <td>3.07</td>
  <td>16.0</td>
</tr>
<tr height="5">
  <td>Maryland</td>
  <td>2.95</td>
  <td>0.75</td>
  <td>6.2</td>
</tr>
<tr height="5">
  <td>Massachusetts</td>
  <td>3.06</td>
  <td>0.76</td>
  <td>6.4</td>
</tr>
<tr height="5">
  <td>Michigan</td>
  <td>3.0</td>
  <td>0.51</td>
  <td>5.2</td>
</tr>
<tr height="5">
  <td>Minnesota</td>
  <td>2.8</td>
  <td>0.83</td>
  <td>6.4</td>
</tr>
<tr height="5">
  <td>Mississippi</td>
  <td>3.38</td>
  <td>2.14</td>
  <td>12.7</td>
</tr>
<tr height="5">
  <td>Missouri</td>
  <td>2.91</td>
  <td>0.72</td>
  <td>6.1</td>
</tr>
<tr height="5">
  <td>Montana</td>
  <td>1.97</td>
  <td>4.67</td>
  <td>22.3</td>
</tr>
<tr height="5">
  <td>Nebraska</td>
  <td>3.81</td>
  <td>3.01</td>
  <td>16.9</td>
</tr>
<tr height="5">
  <td>Nevada</td>
  <td>3.71</td>
  <td>1.9</td>
  <td>12.0</td>
</tr>
<tr height="5">
  <td>New Hampshire</td>
  <td>2.79</td>
  <td>3.26</td>
  <td>17.0</td>
</tr>
<tr height="5">
  <td>New Jersey</td>
  <td>3.46</td>
  <td>0.76</td>
  <td>6.8</td>
</tr>
<tr height="5">
  <td>New Mexico</td>
  <td>3.85</td>
  <td>3.1</td>
  <td>17.3</td>
</tr>
<tr height="5">
  <td>New York</td>
  <td>3.79</td>
  <td>0.19</td>
  <td>4.6</td>
</tr>
<tr height="5">
  <td>North Carolina</td>
  <td>2.83</td>
  <td>0.53</td>
  <td>5.1</td>
</tr>
<tr height="5">
  <td>North Dakota</td>
  <td>2.95</td>
  <td>6.03</td>
  <td>29.2</td>
</tr>
<tr height="5">
  <td>Ohio</td>
  <td>3.07</td>
  <td>0.37</td>
  <td>4.7</td>
</tr>
<tr height="5">
  <td>Oklahoma</td>
  <td>4.41</td>
  <td>1.76</td>
  <td>12.1</td>
</tr>
<tr height="5">
  <td>Oregon</td>
  <td>2.62</td>
  <td>1.17</td>
  <td>7.7</td>
</tr>
<tr height="5">
  <td>Pennsylvania</td>
  <td>3.12</td>
  <td>0.34</td>
  <td>4.6</td>
</tr>
<tr height="5">
  <td>Rhode Island</td>
  <td>4.63</td>
  <td>5.44</td>
  <td>28.3</td>
</tr>
<tr height="5">
  <td>South Carolina</td>
  <td>3.43</td>
  <td>1.22</td>
  <td>8.7</td>
</tr>
<tr height="5">
  <td>South Dakota</td>
  <td>2.7</td>
  <td>6.16</td>
  <td>29.5</td>
</tr>
<tr height="5">
  <td>Tennessee</td>
  <td>3.76</td>
  <td>1.08</td>
  <td>8.5</td>
</tr>
<tr height="5">
  <td>Texas</td>
  <td>4.22</td>
  <td>0.32</td>
  <td>5.6</td>
</tr>
<tr height="5">
  <td>Utah</td>
  <td>3.59</td>
  <td>1.88</td>
  <td>11.8</td>
</tr>
<tr height="5">
  <td>Vermont</td>
  <td>3.39</td>
  <td>6.59</td>
  <td>32.1</td>
</tr>
<tr height="5">
  <td>Virginia</td>
  <td>2.91</td>
  <td>0.67</td>
  <td>5.8</td>
</tr>
<tr height="5">
  <td>Washington</td>
  <td>3.18</td>
  <td>0.63</td>
  <td>5.9</td>
</tr>
<tr height="5">
  <td>West Virginia</td>
  <td>4.37</td>
  <td>3.59</td>
  <td>20.0</td>
</tr>
<tr height="5">
  <td>Wisconsin</td>
  <td>2.88</td>
  <td>0.67</td>
  <td>5.8</td>
</tr>
<tr height="5">
  <td>Wyoming</td>
  <td>3.97</td>
  <td>9.68</td>
  <td>46.1</td>
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

Taking a look at the two extremes, we can see a pretty shocking disparity in representation. A voter in Wyoming has more representative power than a Floridian, a Pennsylvanian, a New Yorker, and a Californian <i>combined</i>. This is purely due to the fact that while each of these five states are represented by two senators, only 400,000 voters pick those two people in Wyoming while over 10,000,000 pick them in each of the other four states. Using state-by-state voter demographics, we can expand the scope of our power metric to compare the average representative power of different demographics to see if any group in particular benefits from this arrangement. Comparisons based on sex and age show fairly similar representation between different groups, but race, political affiliation, and urban/rural delineation produce very unbalanced playing fields. As seen in the tables below, white voters have about 10% more representative power than non-white voters, Republican voters have 28% more than Democratic voters, and rural voters (based on <a href="https://github.com/theatlantic/citylab-data/blob/master/citylab-congress/citylab_cdi.csv">CityLab's classification</a>) have 40% more than urban voters. This is again due to the disparate proportioning of representatives in the Senate and highlights the inherent representative inequity in our country's democracy.

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

On a macroscopic scale, this leads to representation that is disproportionate to the actual populations they represent.<span class="image right"><img src="{{ "/images/HouseResultsByYear_Overall.png" | absolute_url }}" alt="" /><img src="{{ "/images/SenateResultsByYear_Cumulative.png" | absolute_url }}" alt="" /></span> Look at the percentages of elected congressional representatives in each party compared to the number of voters who actually voted for that party shown in the first figure. Wins and votes in the House of Representatives have generally been proportional because the number of representatives is allocated based on population -- until 2010 that is when congressional districts were conveniently redrawn by state governments. Can we talk about 2012 please? Democrats received more votes in aggregate during that election and only received 45% of the delegates. The equivalent graph applied to the Senate is even worse. For each year, we can add up the vote totals for each senator's most recent election (e.g. for 2016, a senator elected in 2014 would contribute their 2014 vote totals) and again compare votes by party to wins by party. As you can see in the second figure, the relationship between these two values is loose at best. Since 2004, the percentage of votes cast for Republican candidates has never exceeded that of Democratic candidates, and yet, four of the seven congresses have had as many or more Republican Senators as Democratic Senators. That doesn't exactly seem fair to me...

So what does this imbalance of representative power lead to? Unpopular ideas becoming law and popular ideas getting ignored. More on this to come...

<!-- Congress after congress of old white dudes rather than the melting pot that America so eagerly describes itself as.

So why does this happen and what can we do to fix it? Lack of voter participation, voter suppression, gerrymandering...

The framers were very intentional in their preambular word choice of forming a <i>more perfect</i> union, implying a good start but plenty of room to improve.

Yes, we have definitely improved upon dictatorships and monarchies, but that's a fairly low bar...

settling for a form of democracy that fulfills the Churchillian addage that "democracy is the worst form of government... except for all the others." -->










