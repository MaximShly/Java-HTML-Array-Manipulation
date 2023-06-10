# Java-HTML-Array-Manipulation
Here we declare two local variables inside of a function and point them both to the same array, however I came across some issues with array references that I would like to share with you.


So Originally I used this as my function:
function getPlayingStyle() {
  let firstTeam = [];
  let secondTeam = [];
  firstTeam = [3, 3, 1, 3];
  secondTeam = firstTeam;
  firstTeam = [4, 1, 4, 1];
  return secondTeam;
}

Notice that I actually create a new array and assign firstTeam to the new array (the one with 4,1,4,1)
WHen secondTeam is returned, it will return the old array with 3,3,1,3.

The version shown in the example file:
function getPlayingStyle() {
  let firstTeam = [3, 3, 1, 3];
  let secondTeam = firstTeam;
  firstTeam[0] = 4;
  firstTeam[1] = 1;
  firstTeam[2] = 4;
  firstTeam[3] = 1;
  return secondTeam;
}

Notice that we go back into the originally declared array in firstTeam and modify the index values one by one.
This preserves the id of the original array, so that when secondTeam is returned it will return the updated version
of the original array.
This is contrary to the version above that I originally did on accident until I learned this fact:
declaring an array with [xyz] will create a new array in memory and discard the old one if there was
one declared orignally, or leave it as an old reference to another variable if you happen to do so.
