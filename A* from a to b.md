# me
pixepon475@notedns.com
123@@


"A* algorithme A to F with H_Table
graph = {
    'A': [('B', 1), ('C', 4)],
    'B': [('D', 3), ('E', 2)],
    'C': [('F', 2), ('G', 8)],
    'D': [('H', 1)],
    'F': [('I', 7)],
}
H_table = {'A': 0,
           'B': 2,
           'C': 5,
           'D': 7,
           'E': 3,
           'F': 5,
           'G': 0,
           'H': 10,
           'I': 9
           }


def path_f_cost(pat):
    g_cost = 0
    for (node, cost) in pat:
        g_cost += cost
    last_node = pat[-1][0]
    h_cost = H_table[last_node]
    f_cost = g_cost + h_cost
    return f_cost, last_node


def a_start(gra, start, goal):
    visited = []
    queue = [[(start, 0)]]
    while queue:
        queue.sort(key=path_f_cost)
        path = queue.pop(0)
        node = path[-1][0]
        if node is visited:
            continue
        visited.append(node)
        if node == goal:
            return path
        else:
            adjacent_nodes = gra.get(node, [])
            for (node2, cost) in adjacent_nodes:
                new_path = path.copy()
                new_path.append((node2, cost))
                queue.append(new_path)


solution = a_start(graph, 'A', 'F')
print('la solution est ', solution)
print("cost solution is ", path_f_cost(solution)[0])


"
