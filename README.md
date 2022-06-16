# DFS and BFS Comparison in Python
The comparison will be done on the basis of length of the final path, length of the search path and the execution time plus the discussion on the memory complexit.

### BFS (Breath First Search):
``` 
from BFSfile import BFS
```
[Breadth-First Search](https://favtutor.com/blogs/breadth-first-search-python#:~:text=Breadth%2DFirst%20Search%20is%20a,graph%20is%20almost%20the%20same.) is a recursive algorithm to search all the vertices of a graph or a tree. BFS in python can be implemented by using data structures like a dictionary and lists. Breadth-First Search in tree and graph is almost the same.

![BFS](https://user-images.githubusercontent.com/47225405/174048178-c1749677-3aaf-42af-ae4f-81451372332e.png)
![BFS2](https://user-images.githubusercontent.com/47225405/174048383-3e225131-0f12-4dd4-80cf-f05df2cdc328.png)

### DFS (Depth First Search):
```
from DFSFile import DFS
```
Traversal means that visiting all the nodes of a graph which can be done through Depth-first search or Breadth-first search in python. Depth-first traversal or [Depth-first Search](https://favtutor.com/blogs/depth-first-search-python#:~:text=Traversal%20means%20that%20visiting%20all,graph%20or%20tree%20data%20structure.) is an algorithm to look at all the vertices of a graph or tree data structure.

![DFS1](https://user-images.githubusercontent.com/47225405/174048858-0564d334-4df7-4797-8cad-8604ffd7a96f.png)
![DFS2](https://user-images.githubusercontent.com/47225405/174048868-f8f92690-1f38-4385-857e-5260af24ecda.png)

### Pyamaze:
```
from pyamaze import maze, agent, COLOR, textLabel
```
The module pyamaze is created for the easy generation of random maze and apply different search algorithm efficiently. The main idea of this module, pyamaze, is to assist in creating customizable random mazes and be able to work on that, like applying the search algorithm with much ease.

### Timeit:
```
from timeit import timeit
```
Python timeit() is a method in Python library to measure the execution time taken by the given code snippet. The Python library runs the code statement 1 million times and provides the minimum time taken from the given set of code snippets.

```diff
+ from BFSfile import BFS
+ from DFSFile import DFS
+ from pyamaze import maze, agent, COLOR, textLabel
+ from timeit import timeit
```
```diff
+ m=maze(15,20) 
```
```diff
# I am creating a maze of size 15 by 20
# m.CreateMaze(loopPercent=100)
# loopercent=100 meaning the maximum number of loops in the maze path
```
```diff
#Internally the last cell i.e. the last row and last column cell is set as the start cell. 
```
```diff
+ m.CreateMaze(3,5,loopPercent=100, theme='light') 
```
```diff
# My goal row and column (3,5)
# With loopPercent we can create a maze with multiple paths.
# loopPercent=100, means it will maximize the number of multiple paths
```
```diff
# and here i have called the function bfs and dfs 
# first is the search path than the reverse path from the goal to the start and the second is the path from start to goal
```
```diff
+ searchPath,dfsPath,fwdDFSPath=DFS(m)
+ bSearch,bfsPath,fwdBFSPath=BFS(m)
```
```diff
# but will simply display the sizes of the two such spaces and then i can easily compare those, 
# in these four lines we are displaying the two such space lengths of the two algorithms and also the length of the final paths calculated by two algorithms
```
```diff
+ textLabel(m,'DFS Path Length',len(fwdDFSPath)+1)
+ textLabel(m,'BFS Path Length',len(fwdBFSPath)+1)
+ textLabel(m,'DFS Search Length',len(searchPath)+1)
+ textLabel(m,'BFS Search Length',len(bSearch)+1)
```
```diff
# Here we are simulating an agent travelling on the path calculated by the algorithms first a blue colored agent will follow the path caculated by bfs and 
# then small size red colored agent will traverse the path calculated by dfs
```
```diff
+ a=agent(m,footprints=True,color=COLOR.blue,filled=True)
+ b=agent(m,footprints=True,color=COLOR.red)
```
```diff
# footprints:I used it to be able to visualize the full path when the agent moves through the maze.
```
```diff
+ m.tracePath({a:fwdBFSPath},delay=100)
+ m.tracePath({b:fwdDFSPath},delay=100)
```
```diff
# Here we are calculating the time taken by the two algorithms to compute the final path for that we are using the time it  function of the time it module 
# for that we need to provide the statement we wnat to execute as a string
```
```diff
+ t1=timeit(stmt='DFS(m)',number=1000,globals=globals())
+ t2=timeit(stmt='BFS(m)',number=1000,globals=globals())
```
```diff
+ t1=timeit(stmt='DFS(m)',number=1000,globals=globals())
+ t2=timeit(stmt='BFS(m)',number=1000,globals=globals())
```
```diff
#timeit: provides the minimum time taken from the given set of code snippets
```
```diff
# Then we need to provide the complete global space of this program to the time it function it is needed 
# because the statement provided here will get exacuted in the time it module and the statement is exacuting function or bfs 
# which are defined in this file so the definition of all variables and functions as tetra are passed to the time it module and then here we are displaying those times
```
```diff
+ textLabel(m,'DFS Time',t1)
+ textLabel(m,'BFS Time',t2)
```
```diff
- finally is the run function to run the simulation before i run this program, DFS doesnt guarentee to provide the shortest path while the BFS quarentees to provide the shortest path
```
```diff
+ m.run()
```
```diff
# the function run to run the simulation
```

![Adsız tasarım (1)](https://user-images.githubusercontent.com/47225405/174049980-787820f5-c1cb-449e-bb96-2aaa73753fe2.png)

