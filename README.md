
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
