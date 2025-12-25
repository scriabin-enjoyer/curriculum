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

In this project, we'll be using an adjacency matrix to represent the graph. We've picked this style of graph because it gives you great practice at adding and removing vertices, and making sure everything stays in sync. However, in future projects (like Knight Travails) you may wish to go for an adjacency list approach, since you have a bit less manual work to do keeping the state in check.

### Assignment

<div class="lesson-content__panel" markdown="1">

You'll build an undirected, unweighted graph implementation using an adjacency matrix. The focus is on understanding how to store and manipulate graph relationships. For simplicity, you may assume that the values of each vertex are unique in the graph.

Build a `Graph` class to represent your graph. For now it should only include storage for a list of `@vertices` and a `@matrix` (or 2D array) to serve as the adjacency matrix. Then proceed to create the following methods:

1. `add_vertex(value)`: Adds a new value to the list of vertices and expands the matrix

   **Hint:** The adjacency matrix should always be of size `n × n` where `n` is the number of vertices.

1. `add_edge(value1, value2)`: Creates an edge between two vertices

    **Tip:** If you would like to visualize your graph, here is a `to_s` function that you can use to print your graph's adjacency matrix in a structured format. Once this method is defined on your `Graph`, you will be able to `puts my_graph`, where `my_graph` is an instance of your `Graph` class. Note that this method prints the indexes of the vertices on the top and to the left of the matrix. This indicates which vertices are associated with which column or row in the matrix.

    ```ruby
    def to_s
      first_row = '  ' + @vertices.length.times.map(&:to_s).join(' ') + "\n"
      other_rows = String.new
      @matrix.each_with_index do |row, i|
        other_rows << "#{i} #{row.join(' ')}\n"
      end
      first_row + other_rows
    end
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
    # The matrix should now look like this:
    #   A B C D
    # A 0 1 1 0
    # B 1 0 1 0
    # C 1 1 0 1
    # D 0 0 1 0

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
