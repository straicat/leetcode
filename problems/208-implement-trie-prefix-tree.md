## 208. Implement Trie (Prefix Tree) - 实现 Trie (前缀树)

<!--If you want to use the English description, use `question.content` instead-->

<p>实现一个 Trie (前缀树)，包含&nbsp;<code>insert</code>,&nbsp;<code>search</code>, 和&nbsp;<code>startsWith</code>&nbsp;这三个操作。</p>

<p><strong>示例:</strong></p>

<pre>Trie trie = new Trie();

trie.insert(&quot;apple&quot;);
trie.search(&quot;apple&quot;);   // 返回 true
trie.search(&quot;app&quot;);     // 返回 false
trie.startsWith(&quot;app&quot;); // 返回 true
trie.insert(&quot;app&quot;);   
trie.search(&quot;app&quot;);     // 返回 true</pre>

<p><strong>说明:</strong></p>

<ul>
	<li>你可以假设所有的输入都是由小写字母&nbsp;<code>a-z</code>&nbsp;构成的。</li>
	<li>保证所有输入均为非空字符串。</li>
</ul>



-----

题目标签：Design / Trie

题目链接：[LeetCode](https://leetcode.com/problems/implement-trie-prefix-tree/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/implement-trie-prefix-tree/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 74  ms | 52.2 MB |

```java
class Trie {
    
    class TrieNode {
        int path;
        int end;
        TrieNode map[];
        
        TrieNode() {
            path = 0;
            end = 0;
            map = new TrieNode[26];
        }
    }
    
    TrieNode root;

    /** Initialize your data structure here. */
    public Trie() {
        root = new TrieNode();
    }
    
    /** Inserts a word into the trie. */
    public void insert(String word) {
        char[] w = word.toCharArray();
        TrieNode node = root;
        int index = 0;
        for (int i = 0; i< w.length; i++) {
            index = w[i] - 'a';
            if (node.map[index] == null) {
                node.map[index] = new TrieNode();
            }
            node = node.map[index];
            node.path++;
        }
        node.end++;
    }
    
    /** Returns if the word is in the trie. */
    public boolean search(String word) {
        char[] w = word.toCharArray();
        TrieNode node = root;
        int index = 0;
        for (int i = 0; i < w.length; i++) {
            index = w[i] - 'a';
            if (node.map[index] == null) {
                return false;
            }
            node = node.map[index];
        }
        return node.end > 0;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    public boolean startsWith(String prefix) {
        char[] w = prefix.toCharArray();
        TrieNode node = root;
        int index = 0;
        for (int i = 0; i < w.length; i++) {
            index = w[i] - 'a';
            if (node.map[index] == null) {
                return false;
            }
            node = node.map[index];
        }
        return true;
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```
