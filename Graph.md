## Graph

#### Notice: Check visited node!!

Directed: |E| = |V|^2  
Undirected: |E| = |V|*(|V|-1)/2 + |V|  
Equal matrix: G(i,j) = G(j,i)  

For both directed and undirected:  
* Speace Complexity    
  * Adjacency Matrix O(V^2)   
  * Adjacency List O(V+E)  
  * Which one is better for sparse?  
* How expensive it is to find (u, v) belongs to E?  
  * Adjacency Matrix O(1)  
  * Adjacency List O(degree(u)) (O(1) to find node and dig in)  
    * Dense worst: O(V)  
    * Sparse: O(1)  

For undirected:  
* How expensive it is to compute the degree of a node?  
  * Adjacency Matrix O(V)   
  * Adjacency List O(degree(u))    

For directed:  
* How expensive it is to compute the out degree of a node?  
  * Adjacency Matrix O(V)   
  * Adjacency List O(degree(u))    
* How expensive it is to compute the in degree of a node?  
  * Adjacency Matrix O(V)   
  * Adjacency List O(V+E)    

# Breadth-First Search (BFS)
1. zig-zag
2. is not for the shortest distance

# Best First Search (BFS)
## Dijkstra
Find the shortest node from a single node to any other node in the graph  

### Q1
Given a matrix of size NxN and for each row and each column the elements are sorted in ascending order. How to find the Nth smallest element in it?  
12345  
23456  
34567  
45678  
56789  



# Depth-First Search (DFS)
Why DFS? 
save space.  
If the tree or map are too deep / have too many layers, it may not be a good option.  

## Q1: Find all subsets of a set  
<img width="636" alt="dfs" src="https://cloud.githubusercontent.com/assets/14355257/20113669/5d6554aa-a5bf-11e6-9d60-0299db53d260.png">
Meaning of each level: whether to add or not add this element into each subset.  

```
void findSubset(String input, int index, String solution)
  if(index == input.length()) 
    if (solutio.size() == 0)
      print "empty"
    else
      print solution
   return

  solution.append(intput.at(index))
  findSubset(input, index+1, solution)
  solution.delete_last(intput.at(index))

  findSubset(input, index+1, solution)
```
**Time Complexity = O(2^N)**

## Q2: Find all valid permutation pairs (n) using parenthesis provided
The implementation is similar to the above one but is conditional   
Left parenthesis added >= Right parenthesis added  
```
dfs() {
  if (r == n && l == n)
    return solution
  if (l<n)
    solution += (
    DFS
    solution.remove_last
  if (r<l)
}
```
## Q3: All possible combinations of coins that sum up to value k
total: 99 cents  
coins: 25, 10, 5, 1 cent  
Solution 1:  
              99
       /     |     |     \          
1st 25(74) 10(89) 5(94) 1(98)   
2nd...
Time: O(4^n)

Solution 2:  
Meaning of each level: one kind of coins, the length is dynamic
                    99
           /     |     |     \          
1st(25) 0(99)  1(74)  2(49) 3(24)   
2st(10)

Time = O(n^4) (worst case, four kinds of one cent)
```
dfs(int amountLeft, int level, int sol[]) {
  if (level == sol.length -1) {
    sol[level] = moneyLeft;
    print(moneyLeft);
    return;
  }
  
  for(int i =0; i * con[level] <= moneyLeft; i++) {
    sol[level] = i;  // i coins of this kind
    dfs(moneyLeft-i*coin[level], level+1, sol);
  }
}
```

## Q4: Given a string with non-duplicated letters, print all permutations of the string.  
e.g.:String input = "abc"     abc acb bac bca cab cba  
Meaning of each level:   
                        abc  
              /          |          \  
level 0  a(remin=bc)   b(ac)         c(ba)    swap each element with element at position "level", don't remove/add        
           /   \       /   \         /   \  
level 1  b(c)  c(b)   a(c)  c(a)    a(b)  b(a)  one less branch for each node  
          |     |     |     |       |     |  
level 2   c     b     c     a       b     a  
```
void permutation (String input, int index) {  // index = level
  if (index == input.length()) {
    syso(input)
    return;
  }
  for(int i = index; i< input.length(); i++) {
    swap(input, index, i);
    permuatation(input, index + 1);
    swap(input, index, i);
  }
}
```
When all elements have to maintain, consider to use swap.
# Reduce the usage of string methods (usually O(N)).
