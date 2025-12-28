### Introduction

A graph is a way to represent connections between things. Think of it like drawing points (called vertices or nodes) and connecting them with lines (called edges). Graphs have a wide variety of applications, and we can use them to model complex relationships. For example:

- In a social network, each person is a vertex, and friendships are edges
- In a road map, cities are vertices, and roads between them are edges
- In a computer network, devices are vertices, and connections between computers are edges

![Basic Graph Visualization](example-image.png)

### Why Use Graphs?

Graphs are incredibly useful for modeling relationships and connections. They help us solve real-world problems like:

1. Finding the shortest route between two cities.
1. Suggesting friends on social media.
1. Planning computer network layouts for reliability and speed.
1. Analysing and managing dependencies when bundling code.
1. Ranking pages based on connections to similar pages by search engines.

There are a handful of types of graphs used to solve this wide variety of problems. Graphs can be either *directed* or *undirected*, and can be either *weighted* or *unweighted*. A quick explanation of these terms:

- Directed: Connections go only one way (if A connects to B, B doesn't necessarily connect to A). Dependencies in our code are directed, since module A importing B means that module B cannot import module A without introducing circular dependencies.
- Undirected: Connections go both ways (if A connects to B, B connects to A). A computer network is likely to be undirected, since connections between any two computers are mutual.
- Weighted: Connections have some numeric weight that specifies something about them. A road map is likely to be weighted, where the weights are the distances between the cities. This allows you to calculate the distance of your journey by adding the weights of the roads along the way.
- Unweighted: All connections are equal - no one connection is more important than any other. A social network is likely to be unweighted, since connections signify only that a friendship exists.

In this project, we will be using the simplest type of graph, an undirected, unweighted graph.

### Representing a Graph

In our code, there are several ways we could represent a graph. Two of the most common representations include *adjacency lists* and *adjacency matrices*. Read this article about [graphs and their representations](https://www.geeksforgeeks.org/graph-and-its-representations/) from GeeksforGeeks to familiarise yourself with these ideas. They have some example code, but don't pay too much attention to this, as it's a little different to the code we'll be writing in this project.

In this project, we'll be using an adjacency list to represent the graph. We've picked this style of graph because it generally requires less manual bookkeeping when adding or removing vertices, making it easier to keep the graph’s state consistent. Adjacency lists also use less space for many real-world graphs and make it simpler to work with a vertex’s immediate neighbors. For these reasons, adjacency lists are often a better fit for modeling the kinds of relationships you'll encounter in practice. If you would like, you can read this article about [the differences between using adjacency lists and adjacency matrices](https://www.geeksforgeeks.org/dsa/comparison-between-adjacency-list-and-adjacency-matrix-representation-of-graph/)

### Assignment

<div class="lesson-content__panel" markdown="1">

You'll build an undirected, unweighted graph implementation using an adjacency list. The focus is on understanding how to store and manipulate graph relationships. For simplicity, you may assume that the values of each vertex are unique in the graph.

Build a `Graph` class to represent your graph. For now, it should only include storage for an `@adjacency_list`. You can use a hash as the underlying storage mechanism for the list. Then proceed to create the following methods:

1. `add_vertex(value)`: Adds a new value to the adjacency list.

1. `add_edge(value1, value2)`: Creates an edge between two vertices

1. `to_s`: Returns a string representation of the underlying adjacency list. Once you implement this method on your `Graph`, you will be able to `puts my_graph`, where `my_graph` is an instance of your `Graph` class. The string representation should look something like this:

    ```text
    X -> ( Y, Z )
    Y -> ( X )
    Z -> ( X )
    ```

1. `vertex?(value)`: Checks if a vertex exists.

1. `adjacent?(value1, value2)`: Checks if two given vertices are adjacent. This means that they are connected by an edge.

1. `remove_vertex(value)`: Removes a vertex and shrinks the matrix. Any edges that were connected to that vertex are now gone.

1. `remove_edge(value1, value2)`: Removes an edge between two vertices, if one exists.

1. `order`: Gets the order of the graph. This is the number of vertices in the graph.

1. `size`: Gets the size of the graph. This is the number of edges in the graph.

1. `degree(value)`: Gets the degree of a given vertex. This is the number of edges that are connected to that vertex.

1. `neighbors(value)`: Lists all vertices that are adjacent to a given vertex.

1. `common_neighbors(value1, value2)`: Lists all vertices that are adjacent to both given vertices.

#### Test Your Graph

1. Create a new Ruby file. Import your `Graph` class using `require_relative`.

1. Create a new instance of your graph.

    ```ruby
    graph = Graph.new
    ```

1. Populate your graph using the `add_vertex(value)` and `add_edge(value1, value2)` methods by copying the following:

   ```ruby
   # Add some vertices
   graph.add_vertex("A")
   graph.add_vertex("B")
   graph.add_vertex("C")
   graph.add_vertex("D")

   # Add some edges
   graph.add_edge("A", "B")
   graph.add_edge("B", "C")
   graph.add_edge("A", "C")
   graph.add_edge("C", "D")
   ```

   **Note:** We're using letters as the vertices here, but they could be anything we wanted. We could be using strings, numbers, or even a custom `Vertex` class.

1. Now you have your graph populated, try out a few of the methods by copying the following:

   ```ruby
    puts graph
    # The list should now look like this:
    # A -> ( B, C )
    # B -> ( A, C )
    # C -> ( A, B, D )
    # D -> ( C )

   p graph.order # => 4
   p graph.size # => 4

   graph.remove_edge('C', 'B')
   p graph.size # => 3

   p graph.neighbors('A') # => ['B', 'C']
   p graph.common_neighbors('A', 'D') # => ['C']
   p graph.common_neighbors('A', 'B')) # => []
   ```

1. Lastly, experiment with different combinations of all the methods you have in your graph! Make sure everything is working as you expect it to.

</div>

### Additional resources

This section contains helpful links to related content. It isn't required, so consider it supplemental.

- It looks like this lesson doesn't have any additional resources yet. Help us expand this section by contributing to our curriculum.
