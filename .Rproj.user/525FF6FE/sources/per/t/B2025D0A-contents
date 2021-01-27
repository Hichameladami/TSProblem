#include <Rcpp.h>
#include <bits/stdc++.h>
#include <iostream>
#include <vector>
using namespace Rcpp;
using namespace std;

// Function to find the minimum
// cost path for all the paths
//[[Rcpp::export]]
void Greedy_2opt_cpp(NumericMatrix tsp)
{
  int sum = 0;
  int counter = 0;
  int j = 0, i = 0;
  int min = INT_MAX;
  map<int, int> visitedRouteList;

  // Starting from the 0th indexed
  visitedRouteList[0] = 1;
  int OBJECTIVE_LIST[tsp.nrow()];
  int adjacency_list[tsp.nrow()];
  // Tour Construction & improvement
  // Traverse the adjacency
  // matrix tsp[][]
  while (i < tsp.nrow() && j < tsp.nrow())
  {

    // Corner of the Matrix
    if (counter >= tsp.nrow() - 1)
    {
      break;
    }

    // If this path is unvisited then
    // and if the cost is less then
    // update the cost
    if (j != i && (visitedRouteList[j] == 0))
    {
      if (tsp(i,j) < min)
      {
        min = tsp(i,j);
        OBJECTIVE_LIST[counter] = j + 1;
      }
    }
    j++;

    //Check the goodness of the new adjacency list

    if (j == tsp.nrow())
    {
      sum += min;
      min = INT_MAX;
      visitedRouteList[OBJECTIVE_LIST[counter] - 1] = 1;
      j = 0;
      i = OBJECTIVE_LIST[counter] - 1;
      //printf("%d->%d",i,j);
      counter++;
    }

  }

  // Update the ending city in array
  i = OBJECTIVE_LIST[counter - 1] - 1;

  for (j = 0; j < tsp.nrow(); j++)
  {
    if ((i != j) && tsp(i,j) < min)
    {
      min = tsp(i,j);
      OBJECTIVE_LIST[counter] = j + 1;
      adjacency_list[j]=i;

    }
  }
  sum += min;

  for (j = 0; j < tsp.nrow(); j++){
    printf("%d->",OBJECTIVE_LIST[j]);
  }

  cout << ("Minimum Cost is : ");
  cout << (sum);

}
