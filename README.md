# CGforISDP
This repository contains the instances used in the paper "The Chvatal-Gomory Procedure for Integer SDPs with Applications in Combinatorial Optimization", by Frank de Meijer and Renata Sotirov.

In total there are three type of instances in this repository: the bioinformatics instances, the reload instances and the grid instances. 

------------------------------------------------------------------------------------------------------------------------------------------
Bioinformatics instances:

The underlying graph G is the complete graph on n nodes. The given instances are in .aqtsp format, which are structured as follows: 

n  // (number of vertices)
for i = 1:n
  for j = 1:n
    for k = 1:n
       if (i == j || i == k || j == k) continue;
       costs(i,j,k)
    end
  end
end

------------------------------------------------------------------------------------------------------------------------------------------
Reload instances:

The reload files are .aqtsp instances identified as "rel_n_i_p_c_s" where: 
    n - number of nodes in graph
    i - identifies index of the instance for given value of n, p, c and s. For each combination of n, p, c and s we consider instances for i = 1, ..., 10. 
    p - density of the graph: p = 5 for density 0.5, p = 10 for density 1
    c - number of colors in reload function
    s - reload class: s = 0 for class 1 and s = 1 for class 2
    
The given files are again .aqtsp instances and are structured similar as the bioinformatics instances. The only difference is that costs(i,j,k) = -1 whenever a certain two-arc is not in the graph G. This can only happen if p = 5. Whenever costs(i,j,k) = -1 for all possible k, this implies that arc (i,j) is not present in G. 

------------------------------------------------------------------------------------------------------------------------------------------
Grid instances:

The grid instances are .txt files containing the coordinates of the nodes. Each line contains the Euclidean coordinates (x_i,y_i) for a given node i. The underlying graph G is such that edge {i,j} is present whenever (x_i = x_j and |y_i - y_j| = 1) or (y_i = y_j and |x_i - x_j| = 1). The quadratic cost q_{ijk} is calculated using the formula given on page 26 of the preprint. 
