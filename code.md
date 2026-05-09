# Assignment-3
import random
```python
# ---------- Graph Definition ----------
# Example graph using adjacency list
graph = {
    0: [1, 2],
    1: [0, 2, 3],
    2: [0, 1, 3, 4],
    3: [1, 2, 4],
    4: [2, 3]
}

# ---------- Greedy Coloring ----------
def greedy_coloring(graph, order):
    color = {}

    for vertex in order:
        used_colors = set()

        # Collect colors of neighbors
        for neighbor in graph[vertex]:
            if neighbor in color:
                used_colors.add(color[neighbor])

        # Assign smallest available color
        current_color = 0
        while current_color in used_colors:
            current_color += 1

        color[vertex] = current_color

    return color


# ---------- Validation ----------
def is_valid_coloring(graph, coloring):
    for vertex in graph:
        for neighbor in graph[vertex]:
            if coloring[vertex] == coloring[neighbor]:
                return False
    return True


# ---------- Orders ----------
vertices = list(graph.keys())

# 1. Natural order
natural_order = vertices[:]

# 2. Random order
random_order = vertices[:]
random.shuffle(random_order)

# 3. Highest-degree-first
degree_order = sorted(vertices,
                      key=lambda v: len(graph[v]),
                      reverse=True)

orders = {
    "Natural Order": natural_order,
    "Random Order": random_order,
    "Highest Degree First": degree_order
}

# ---------- Run Tests ----------
for name, order in orders.items():
    print(f"\n{name}")
    print("Processing order:", order)

    coloring = greedy_coloring(graph, order)

    print("Vertex Colors:")
    for vertex in sorted(coloring):
        print(f"Vertex {vertex} -> Color {coloring[vertex]}")

    total_colors = max(coloring.values()) + 1

    print("Total colors used:", total_colors)
    print("Valid coloring:", is_valid_coloring(graph, coloring))
