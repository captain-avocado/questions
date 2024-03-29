# Основные структуры данных

## Графы. Деревья

**Граф** – множество вершин и множество ребер, которые образуют соединения между вершинами. 

1. *Ориентированный граф* – граф, ребрам которого присвоено направление. 

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a2/Directed.svg/1920px-Directed.svg.png" width="200">

2. Если ни одному ребру графа не присвоено направление, то он называется *неориентированным*. Смешанный граф - граф, в котором ребра могут ориентированными или неоринтированными.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Undirected.svg/1920px-Undirected.svg.png" width="200">

2. - Маршрут – конечная последовательность вершин, каждая из которых соединена со следующей в последовательности вершиной и ребром.
   - Цепь – маршрут без повторяющихся ребер.
   - Цикл – цепь, в котором первая и последняя вершины совпадают.
3. *Связный граф* – граф, в котором между любой парой вершин существует как минимум один путь.
4. **Дерево** - связный граф без циклов.


## DFS, BFS.

Поиск в глубину (DFS)

<img src="https://camo.githubusercontent.com/aaad9e39961daf34d967c616edeb50abf3bf1235/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f372f37662f44657074682d46697273742d5365617263682e676966" width="200">

Поиск в ширину (BFS)

<img src="https://camo.githubusercontent.com/b8073f26dfdf1644e8a92312fff100341987a8f5/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f352f35642f427265616474682d46697273742d5365617263682d416c676f726974686d2e676966" width="200">
