# 🧰 Java Cheat Sheet for Leetcode

A practical guide to Java collections commonly used in algorithm and data structure problems on Leetcode.

---

## 📦 1. Arrays

- **Type**: Fixed-size container
- **Declaration**:
  ```java
  int[] arr = new int[5];
  int[] arr = {1, 2, 3};
  ```
- **Access**: `arr[i]`
- **Length**: `arr.length`
- **Use Case**: Fast index access, constant size data

---

## 🧾 2. List (usually `ArrayList`)

- **Type**: Dynamic array
- **Import**: `import java.util.*;`
- **Declaration**:
  ```java
  List<Integer> list = new ArrayList<>();
  ```
- **Access**: `list.get(i)`
- **Size**: `list.size()`
- **Use Case**: Resizable array, storing ordered elements

---

## 🔁 3. LinkedList

- **Type**: Doubly linked list
- **Declaration**:
  ```java
  LinkedList<Integer> list = new LinkedList<>();
  ```
- **Access**: `list.getFirst()`, `list.addLast(x)`, `list.removeFirst()`
- **Use Case**: Queue, Deque, sliding window problems

---

## 🧺 4. Queue (FIFO)

- **Type**: Interface, usually backed by `LinkedList` or `ArrayDeque`
- **Declaration**:
  ```java
  Queue<Integer> q = new LinkedList<>();
  ```
- **Methods**: `offer(x)`, `poll()`, `peek()`
- **Use Case**: BFS, level-order traversal

---

## 📥 5. Stack (LIFO)

- **Declaration**:
  ```java
  Deque<Integer> stack = new ArrayDeque<>();
  ```
- **Methods**: `push(x)`, `pop()`, `peek()`
- **Use Case**: Backtracking, parentheses validation, monotonic stack

---

## 🔍 6. Set

- **Type**: Unordered collection of unique elements
- **Declaration**:
  ```java
  Set<Integer> set = new HashSet<>();
  ```
- **Methods**: `add(x)`, `contains(x)`, `remove(x)`
- **Use Case**: Membership check, deduplication, visited set

---

## 🗝️ 7. Map (HashMap, TreeMap)

- **Type**: Key-value mapping
- **Declaration**:
  ```java
  Map<Character, Integer> map = new HashMap<>();
  ```
- **Methods**: `put(k, v)`, `get(k)`, `containsKey(k)`, `remove(k)`
- **Use Case**: Frequency counter, prefix sum, lookup table

---

## 📊 8. PriorityQueue (Heap)

- **Type**: Min-heap by default
- **Declaration**:
  ```java
  PriorityQueue<Integer> minHeap = new PriorityQueue<>();
  PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
  ```
- **Methods**: `add(x)`, `poll()`, `peek()`
- **Use Case**: Top-K elements, Dijkstra, greedy problems

---

## 🪜 9. Deque

- **Type**: Double-ended queue
- **Declaration**:
  ```java
  Deque<Integer> dq = new ArrayDeque<>();
  ```
- **Methods**: `addFirst()`, `addLast()`, `removeFirst()`, `removeLast()`
- **Use Case**: Sliding window max/min, Monotonic queue

---

## 🧩 10. TreeSet / TreeMap

- **Type**: Sorted version of Set/Map
- **Declaration**:
  ```java
  TreeSet<Integer> ts = new TreeSet<>();
  TreeMap<Integer, String> tm = new TreeMap<>();
  ```
- **Use Case**: Range queries, order statistics, ceiling/floor operations

---

## 🔁 11. Iterator

- **Used For**: Safe removal during iteration
- **Declaration**:
  ```java
  Iterator<Integer> it = set.iterator();
  while (it.hasNext()) {
      int x = it.next();
      if (condition) it.remove();
  }
  ```

---

## 📌 Summary Table

| Structure        | Key Methods                          | Common Leetcode Use Cases                    |
|------------------|--------------------------------------|----------------------------------------------|
| `Array`          | `arr[i]`, `arr.length`               | DP, prefix sum, binary search                |
| `ArrayList`      | `add`, `get`, `size`                 | General purpose, 2D grid                     |
| `LinkedList`     | `addFirst`, `removeLast`             | Queue, Deque, sliding window                 |
| `Queue`          | `offer`, `poll`, `peek`              | BFS, level-order traversal                   |
| `Stack` (Deque)  | `push`, `pop`, `peek`                | DFS, parenthesis, monotonic stack            |
| `HashSet`        | `add`, `contains`, `remove`          | Uniqueness, visited set                      |
| `HashMap`        | `put`, `get`, `containsKey`          | Frequency, prefix sums, grouping             |
| `PriorityQueue`  | `add`, `poll`, `peek`                | Greedy, top-K, shortest path                 |
| `Deque`          | `addFirst`, `removeLast`             | Sliding window max/min                       |
| `TreeMap`        | `ceilingKey`, `floorKey`             | Range queries, sorted access                 |

---

📚 Common mistakes

## 1. 🔢 `length` vs `length()` vs `size()`

| Type       | Access        | Example              | Notes                                |
|------------|---------------|----------------------|--------------------------------------|
| Array      | `.length`     | `arr.length`         | Public field, no `()`                |
| String     | `.length()`   | `str.length()`       | Method call                          |
| List/Set   | `.size()`     | `list.size()`        | Method, not `.length()`              |

✅ **Rule of Thumb**  
- Arrays → `.length`  
- Strings → `.length()`  
- Collections → `.size()`

---

## 2. 🔍 Indexing

| Type       | Access Style    | Example               | Notes                               |
|------------|------------------|-----------------------|-------------------------------------|
| Array      | `arr[i]`         | `arr[2]`              | Valid for primitive arrays          |
| String     | `.charAt(i)`     | `str.charAt(1)`       | ❌ No `str[i]` in Java               |
| List       | `.get(i)`        | `list.get(0)`         | ❌ No `list[i]`                      |
| Set/Map    | ❌ No indexing    | Use `.contains()` or `.get()` | No positional access       |

✅ **Rule of Thumb**  
- Use `[]` only for arrays  
- Use `.charAt()` for `String`  
- Use `.get()` for `List` and `Map`

---

## 3. 🗝️ Set and Map Access

| Operation         | Set Syntax          | Map Syntax                   | Notes                         |
|-------------------|---------------------|-------------------------------|-------------------------------|
| Add               | `set.add(x)`        | `map.put(k, v)`              |                              |
| Contains          | `set.contains(x)`   | `map.containsKey(k)`         |                              |
| Get value         | ❌ (no access)       | `map.get(k)`                 |                              |
| Iterate           | `for (T x : set)`   | `for (Map.Entry<K,V> entry : map.entrySet())` | Use for key+value access |

---

## 4. 🔁 Iteration Patterns

| Collection | Best Loop Syntax                      | Notes                                |
|------------|----------------------------------------|--------------------------------------|
| Array      | `for (int x : arr)`                   | or use index: `arr[i]`               |
| String     | `for (int i = 0; i < s.length(); i++)`<br>`s.charAt(i)` | No `[]`                              |
| List       | `for (T x : list)`<br>`list.get(i)`   | Use `.get()` if index needed         |
| Set        | `for (T x : set)`                     | No `[]`, no index                    |
| Map        | `for (Map.Entry<K,V> entry : map.entrySet())` | Cleanest way to access key + value |

✅ **Use Iterators** when removing during traversal.

---
