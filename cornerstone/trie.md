<h1 align="center">
<br>
	<a href="https://www.wikiwand.com/en/Trie">
  <img src="https://i.imgur.com/w7j1TTW.gif" alt="Trie" width=42%">
  </a>
  <br><br>
Trie
  <br><br>
</h1>

> In computer science, a trie, also called digital tree or prefix tree, is a kind of search tree—**an ordered tree data structure** used to store a dynamic set or associative array where the keys are usually strings. [[wiki](https://www.wikiwand.com/en/Trie)]

## 📝1. Basics

Tries are special trees (prefix trees) that make searching and storing strings more efficient. Tries have many practical applications, such as conducting **searches** and providing **autocomplete**. It is helpful to know these common applications so that you can easily identify when a problem can be efficiently solved using a trie.

Sometimes preprocessing a dictionary of **words** (given in a list) into a trie, will improve the efficiency of searching for a word of length k, among n words. Searching becomes O(k) instead of O(n).

Be familiar with implementing, from scratch, a Trie class and its `add`, `remove` and `search` methods.

## ⚔️2. Use cases

- implement trie [208](https://leetcode.com/problems/implement-trie-prefix-tree/description/)
- search(string): 421 


## 🤺3. Best Practices

- build a trie 
- [delete subtrie bwtween two words](https://repl.it/@WillWang42/delete-subtrie-recursively)
- BFS in a trie: 1032 

### build a trie

inspired by [severb](https://leetcode.com/problems/add-and-search-word-data-structure-design/discuss/59555/python-trie-with-defaultdict-trick)

``` python
def _trie():
    return collections.defaultdict(_trie)  
```
``` python
trie = lambda : collections.defaultdict(_trie)   
```


### [words to trie](https://repl.it/@WillWang42/trie)

``` python
def build_trie(words):
  trie = _trie()
  for _, word in enumerate(words):
      functools.reduce(dict.__getitem__, word, trie)["#"] = None
```

### implement trie

``` python 
# 208. Implement Trie (Prefix Tree)

class Trie:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.root = {}
        
    def insert(self, word):
        """
        Inserts a word into the trie.
        :type word: str
        :rtype: void
        """
        cur = self.root 
        for c in word:
            if c not in cur:
                cur[c] = {}
            cur = cur[c]
        cur['#'] = '#'
        
    def search(self, word):
        """
        Returns if the word is in the trie.
        :type word: str
        :rtype: bool
        """
        cur = self.root
        for c in word:
            if c not in cur:
                return False 
            cur = cur[c]
        if '#' in cur:
            return True
        return False 
                
    def startsWith(self, prefix):
        """
        Returns if there is any word in the trie that starts with the given prefix.
        :type prefix: str
        :rtype: bool
        """
        cur = self.root 
        for c in prefix:
            if c not in cur:
                return False 
            cur = cur[c]
        return True 
        

# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix) 
```

## 😈4. More training

- [211. Add and Search Word - Data structure design](https://leetcode.com/problems/add-and-search-word-data-structure-design/description/)
- [212. Word Search II](https://leetcode.com/problems/word-search-ii/description/) 🌟
- [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/description/)
- [642. Design Search Autocomplete System](https://leetcode.com/problems/design-search-autocomplete-system/description/)
- [720. Longest Word in Dictionary](https://leetcode.com/problems/longest-word-in-dictionary/)
- [1032. Stream of Characters](https://leetcode.com/problems/stream-of-characters/)


## 💬5. Explanation

## ⚠️6. FAQs

#### Q: What are pros and cons of Trie?

A: 

Pros:

1. With Trie, we can insert and find strings in O(L) time where L represent the length of a single word. This is obviously faster that BST. This is also faster than Hashing because of the ways it is implemented. We do not need to compute any hash function. No collision handling is required (like we do in open addressing and separate chaining)
2. Another advantage of Trie is, we can easily print all words in alphabetical order which is not easily possible with hashing.
3. We can efficiently do prefix search (or auto-complete) with Trie.

Cons: 

The main disadvantage of tries is that they need lot of memory for storing the strings. For each node we have too many node pointers(equal to number of characters of the alphabet), If space is concern, then Ternary Search Tree can be preferred for dictionary implementations. In Ternary Search Tree, time complexity of search operation is O(h) where h is height of the tree. Ternary Search Trees also supports other operations supported by Trie like prefix search, alphabetical order printing and nearest neighbor search.

The final conclusion is regarding tries data structure is **that they are faster but require huge memory for storing the strings.**



source: [Geeks Trie](https://www.geeksforgeeks.org/advantages-trie-data-structure/)

