Traversal
======

## Iterate an iterable item

- `for`: the pointer of an iterable item will be **UNCHANGED** after start
- `while`: the pointer of an iterable item will be **RE-FETCHED** before every loop start

### Dynamically extend an iterable item in `for` loop

- scenario: BFS
- example:
  - [binary_tree_serialization.py](../module/binary_tree_serialization.py)
- the behavior below just like `queue`

```python
>>> arr = [0]
>>> for child in arr:
...     if len(arr) > 5:
...             break
...     arr.append(1)
>>> arr
[0, 1, 1, 1, 1, 1]
```

### Dynamically re-assign an iterable item

1. Normal Form

- scenario: BFS in level traversal
- example:
  - [binary_tree_preorder_traversal.py](../module/binary_tree_preorder_traversal.py)
  - [69_binary_tree_level_order_traversal.py](../lintcode/69_binary_tree_level_order_traversal.py)
  - [598_zombie_in_matrix.py](../lintcode/598_zombie_in_matrix.py)

```python
>>> arr = [{
...     'val': 1,
...     'left': {'val': 2, 'left': None, 'right': None},
...     'right': {'val': 3, 'left': None, 'right': None},
... }]
>>> _arr = None
>>> level = 0
>>> while arr:
...     level += 1
...     _arr = []
...     for child in arr:
...         if child['left']:
...             _arr.append(child['left'])
...         if child['right']:
...             _arr.append(child['right'])
...     arr = _arr
>>> level
2
```

2. Dedup Form

- scenario: BFS in level traversal if the node may be visited twice. e.g., graph.
- example:
  - [lintcode/120_word_ladder.py](../lintcode/120_word_ladder.py)
  - [lintcode/121_word_ladder_ii.py](../lintcode/121_word_ladder_ii.py)
  - [lintcode/531_six_degrees.py](../lintcode/531_six_degrees.py)
