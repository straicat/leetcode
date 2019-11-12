## 877. Stone Game - 石子游戏

<!--If you want to use the English description, use `question.content` instead-->

<p>亚历克斯和李用几堆石子在做游戏。偶数堆石子<strong>排成一行</strong>，每堆都有正整数颗石子&nbsp;<code>piles[i]</code>&nbsp;。</p>

<p>游戏以谁手中的石子最多来决出胜负。石子的总数是奇数，所以没有平局。</p>

<p>亚历克斯和李轮流进行，亚历克斯先开始。 每回合，玩家从行的开始或结束处取走整堆石头。 这种情况一直持续到没有更多的石子堆为止，此时手中石子最多的玩家获胜。</p>

<p>假设亚历克斯和李都发挥出最佳水平，当亚历克斯赢得比赛时返回&nbsp;<code>true</code>&nbsp;，当李赢得比赛时返回&nbsp;<code>false</code>&nbsp;。</p>

<p>&nbsp;</p>

<p><strong>示例：</strong></p>

<pre><strong>输入：</strong>[5,3,4,5]
<strong>输出：</strong>true
<strong>解释：</strong>
亚历克斯先开始，只能拿前 5 颗或后 5 颗石子 。
假设他取了前 5 颗，这一行就变成了 [3,4,5] 。
如果李拿走前 3 颗，那么剩下的是 [4,5]，亚历克斯拿走后 5 颗赢得 10 分。
如果李拿走后 5 颗，那么剩下的是 [3,4]，亚历克斯拿走后 4 颗赢得 9 分。
这表明，取前 5 颗石子对亚历克斯来说是一个胜利的举动，所以我们返回 true 。
</pre>

<p>&nbsp;</p>

<p><strong>提示：</strong></p>

<ol>
	<li><code>2 &lt;= piles.length &lt;= 500</code></li>
	<li><code>piles.length</code> 是偶数。</li>
	<li><code>1 &lt;= piles[i] &lt;= 500</code></li>
	<li><code>sum(piles)</code>&nbsp;是奇数。</li>
</ol>



-----

题目标签：Minimax / Math / Dynamic Programming

题目链接：[LeetCode](https://leetcode.com/problems/stone-game/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/stone-game/description/)

## 题解



| Language | Runtime | Memory |
|:---:|:---:|:---:|
| rust  | 0  ms | 2.4 MB |

```rust
impl Solution {
    pub fn stone_game(piles: Vec<i32>) -> bool {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| php  | 12  ms | 15 MB |

```php
class Solution {

    /**
     * @param Integer[] $piles
     * @return Boolean
     */
    function stoneGame($piles) {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| kotlin  | 192  ms | N/A |

```kotlin
class Solution {
    fun stoneGame(piles: IntArray): Boolean {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| scala  | 296  ms | N/A |

```scala
object Solution {
    def stoneGame(piles: Array[Int]): Boolean = {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| golang  | 0  ms | N/A |

```golang
func stoneGame(piles []int) bool {
    return true;
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| swift  | 8  ms | N/A |

```swift
class Solution {
    func stoneGame(_ piles: [Int]) -> Bool {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| ruby  | 44  ms | N/A |

```ruby
# @param {Integer[]} piles
# @return {Boolean}
def stone_game(piles)
    return true
end
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| javascript  | 68  ms | N/A |

```javascript
/**
 * @param {number[]} piles
 * @return {boolean}
 */
var stoneGame = function(piles) {
    return true;
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| csharp  | 96  ms | N/A |

```csharp
public class Solution {
    public bool StoneGame(int[] piles) {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| c  | 0  ms | N/A |

```c
bool stoneGame(int* piles, int pilesSize) {
    return true;
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| java  | 3  ms | N/A |

```java
class Solution {
    public boolean stoneGame(int[] piles) {
        return true;
    }
}
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| cpp  | 4  ms | N/A |

```cpp
class Solution {
public:
    bool stoneGame(vector<int>& piles) {
        return true;
    }
};
```


| Language | Runtime | Memory |
|:---:|:---:|:---:|
| python3  | 36  ms | N/A |

```python3
class Solution:
    def stoneGame(self, piles):
        """
        :type piles: List[int]
        :rtype: bool
        """
        return True
```
