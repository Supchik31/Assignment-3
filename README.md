# Assignment-3
##My comments and observations about the heuristic
###
Greedy coloring does not always give the optimal answer
The algorithm is fast and simple, but the number of colors depends heavily on the order of vertices.
Different orders can produce different results for the same graph.
Highest-degree-first usually works better
Coloring vertices with many neighbors first often reduces the total number of colors.
This heuristic is commonly more efficient than natural or random order.
Random order is unpredictable
Sometimes it may accidentally produce a very good coloring, but in other cases it may use more colors than necessary.
Natural order is the simplest approach
It is easy to implement, but it ignores graph structure, so it may not produce the best coloring.
The algorithm is efficient for large graphs
Exact graph coloring is an NP-hard problem, so greedy heuristics are practical for real systems where speed is more important than perfect optimality.
