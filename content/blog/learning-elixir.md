---
title: "Learning Elixir"
date: 2023-10-25
draft: false
categories:
    - Elixir
---
第 N 次學習 Functional Programming Language 就上手。

不論是上古神獸 Lisp，Haskell，或是現代一點的 Scala，如果你跟我一樣嘗試過學習 Functional Programming Language，但是都沒有成功，那麼 Elixir 是你最好的選擇。

# Pipe Operation - 括號終結者

我朋友 ypcat 推我入 Elixir 的坑的時候，舉出了一個 Elixir 的優點，那就是 Elixir 的語法很簡單，很像 Ruby，所以學習起來很容易，最重要的是可讀性很高，沒有一堆括號()。

比如說我們要把字串的前後空白去掉，再轉成大寫，然後把 WORLD 換成 Gary，如果用 Python 寫的話，會是這樣：

```
astr = " Hello world! "
astr.strip().upper().replace("WORLD", "Gary")
```
這邊可以看到由於 Python 支援 object ，所以字串有 strip, upper, replace 這些 method 可以用，而且這些 method 都會回傳一個新的字串，所以可以一直串起來用。

再來看一下 Elixir 的寫法：

```
astr = " Hello world! "
String.trim(String.replace(String.upcase(astr), "WORLD", "Gary"))
```

巢狀的括號看起來是不是很難懂? 這時候就可以用到 Pipe Operation 來改寫：

```
astr = " Hello world! "
astr |> String.trim() |> String.upcase() |> String.replace("WORLD", "Gary")
```

背後的原則是，我們可以把這樣的 expression `g(f(x))` 改寫成 `x |> f() | > g()` ，這樣看起來是不是清爽多了？

# Thinking Elixir 入門課程

初次學習 Elixir 的朋友， 推薦從這邊開始，有兩堂入門的課程：
 [ThinkingElixir](https://thinkingelixir.com/available-courses/pattern-matching/)

如果你還沒有 Elixir 的環境，建議可以從 [Livebook](https://livebook.dev/) 開始，Livebook 是一個可以在瀏覽器上執行 Elixir 程式的環境，可以很快的上手 Elixir 的語法。

# Elixir 的資料結構

先來比較一下 python 跟 Elixir 的資料結構，特別注意 Elixir 是 functional programming language，所以資料結構都是 immutable 的，
而且沒有 object method，不管是 List 或是 Map 存取都是用 function。

## List
Elixir 的 List 跟 Python 的 List 很像，但是同樣的 Elixir 的 List 是 immutable 的，如果修改 List 內的值，會得到新的 List 。
另外 Elixir 的 List 不像是 Array，不能直接存取第 n 個元素。一般 List 的用途是要搭配Pattern，例如 [head | tail] ，之後再說明。

## Tuple
Python 的 Tuple 跟 Elixir 的 Tuple 很像，但是 Elixir 的 Tuple 是 immutable 的。

    # Python
    data = (1, 2, "GO") # Python
    data[0] # 1
    data[2] # "GO"

    # Elixir
    data = {1, 2, "GO"}
    elem(data, 0) # 1
    elem(data, 2) # "GO"
    put_elem(t, 2, "foo") # 修改第二個值會傳回一個新的 tuple {1, 2, "foo"}

## Map
Elixir 的 Map 跟 Python 的 Dictionary 很像，但是同樣的 Elixir 的 Map 是 immutable 的，如果修改 Map 內的值，會得到新的 Map 。

Python: Dictionary

    data = { "name" : "gary" , "age": 99 }

Elixir: Map

產生 Map

    data = %{ name: "gary", age: 99, city: "Tokyo" }

注意這裡的 name 是一個 atom (:name)

讀取 Map

    data[:name]

寫入 Map

    Map.put(data, :name, "bob")

更新 Map

    %{data | age: 31, city: "Taipei"}
