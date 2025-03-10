# [1917. Leetcodify Friends Recommendations](https://leetcode.cn/problems/leetcodify-friends-recommendations)

[English Version](/solution/1900-1999/1917.Leetcodify%20Friends%20Recommendations/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>表： <code>Listens</code></p>

<pre>+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| user_id     | int     |
| song_id     | int     |
| day         | date    |
+-------------+---------+
这个表没有主键，可能存在重复项。
表中的每一行表示用户 user_id 在 day 这一天收听的歌曲 song_id。
</pre>

<p>&nbsp;</p>

<p>表： <code>Friendship</code></p>

<pre>+---------------+---------+
| Column Name   | Type    |
+---------------+---------+
| user1_id      | int     |
| user2_id      | int     |
+---------------+---------+
(user1_id, user2_id) 是这个表的主键。
表中的每一行表示 user1_id 和 user2_id 是好友。
注意，user1_id &lt; user2_id。
</pre>

<p>&nbsp;</p>

<p>写出 SQL 语句，为 Leetcodify 用户推荐好友。我们将符合下列条件的用户 <code>x</code> 推荐给用户 <code>y</code> ：</p>

<ul>
	<li>用户 <code>x</code> 和 <code>y</code> 不是好友，且</li>
	<li>用户 <code>x</code> 和 <code>y</code> 在<strong>同一天</strong>收听了相同的三首或更多不同歌曲。</li>
</ul>

<p>注意，好友推荐是<strong>单向</strong>的，这意味着如果用户 <code>x</code> 和用户 <code>y</code> 需要互相推荐给对方，结果表需要将用户 <code>x</code> 推荐给用户 <code>y</code> 并将用户 <code>y</code> 推荐给用户 <code>x</code>。另外，结果表不得出现重复项（即，用户 <code>y</code> 不可多次推荐给用户 <code>x</code> ）。</p>

<p>按<strong>任意顺序</strong>返回结果表。</p>

<p>查询格式如下示例所示：</p>

<p>&nbsp;</p>

<p><strong>示例 1:</strong></p>

<pre><strong>输入：</strong>
Listens 表：
+---------+---------+------------+
| user_id | song_id | day        |
+---------+---------+------------+
| 1       | 10      | 2021-03-15 |
| 1       | 11      | 2021-03-15 |
| 1       | 12      | 2021-03-15 |
| 2       | 10      | 2021-03-15 |
| 2       | 11      | 2021-03-15 |
| 2       | 12      | 2021-03-15 |
| 3       | 10      | 2021-03-15 |
| 3       | 11      | 2021-03-15 |
| 3       | 12      | 2021-03-15 |
| 4       | 10      | 2021-03-15 |
| 4       | 11      | 2021-03-15 |
| 4       | 13      | 2021-03-15 |
| 5       | 10      | 2021-03-16 |
| 5       | 11      | 2021-03-16 |
| 5       | 12      | 2021-03-16 |
+---------+---------+------------+
Friendship 表：
+----------+----------+
| user1_id | user2_id |
+----------+----------+
| 1        | 2        |
+----------+----------+
<strong>输出：</strong>
+---------+----------------+
| user_id | recommended_id |
+---------+----------------+
| 1       | 3              |
| 2       | 3              |
| 3       | 1              |
| 3       | 2              |
+---------+----------------+
<strong>解释</strong>
用户 1 和 2 在同一天收听了歌曲 10、11 和 12，但他们已经是好友了。
用户 1 和 3 在同一天收听了歌曲 10、11 和 12。由于他们不是好友，所以我们给他们互相推荐为好友。
用户 1 和 4 没有收听三首相同的歌曲。
用户 1 和 5 收听了歌曲 10、11 和 12，但不是在同一天收听的。

类似地，我们可以发现用户 2 和 3 在同一天收听了歌曲 10、11 和 12，且他们不是好友，所以我们给他们互相推荐为好友。
</pre>

## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **SQL**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```sql

```

<!-- tabs:end -->
