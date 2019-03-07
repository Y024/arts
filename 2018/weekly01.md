[ARTS(Algorithm + Review + Tip + Share)](https://mntfun.slack.com) 是[耗叔](https://weibo.com/haoel)发起的一个旨在提升大家算法、英语、技术、影响力的活动：

> * **A**lgorithm 部分：在[LeetCode](https://leetcode.com/problemset/all/)上面挑选自己感兴趣的任一道题目进行解答。
> * **R**eview 部分：阅读并点评一篇英文技术文章（可以挑选[湾区日报](https://wanqu.co/)、[Meduim](https://medium.com/)上的文章）。
> * **T**ip 部分：至少学习一个技术技巧。
> * **S**hare 部分：分享一篇有观点和思考的技术文章。

---

## [Algorithm](#algorithm)
> [177. Nth Highest Salary](https://leetcode.com/problems/nth-highest-salary/)

* **What** 找出 `Employee` 表中的第 `n` 高收入。

* **How** `Limit n, m` **n-跳过的行数（从 0 开始计数），m-显示的记录数**。同时需要注意不存在的情况（主要是存在多条收入一致的，则只算为一条）。

* **Key Codes** 
```sql
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
  SET N = N -1;
  RETURN (
      # Write your MySQL query statement below.
      select ifnull((select distinct Salary from Employee order by Salary desc limit N,1), null) SecondHighestSalary
  );
END
```

## [Review](#review)
> [When and why to clean up your code: now, later, never](https://codewithoutrules.com/2018/11/02/when-clean-up-your-code/)

* **What** 发布期限马上到了，你必须修改 bug，也必须按期发布产品。但你又需要未雨绸缪：现在引入的 bug，如果后续再改将耗费更多的时间；那些过期的依赖、废弃的 API，也不该出现在你代码里。现实与理解的纠缠，该怎么处理你的技术债？现在，将来，还是从不？

* **How** 涉及三种处理方式：更新（过期依赖、废弃的 API），重构不佳的抽象，（代码规范等）杂项。根据所处周期（原型期、全新的工程、紧急修复、新功能或非紧急修复、处于维护期）不同，分别对应不同的处理策略。

|   | Updating | Refactoring | Miscellaneous Cleanups |
|---:|---:|---:|---:|
|Prototyping|never|now if you’re trying to prototype an API or abstraction, otherwise never.|never
|A new project|now|now|now|
|An emergency bugfix|later|later|later|
|New feature or non-urgent bugfix|now, for code you’re touching.|now, for code you’re touching.|now, for code you’re touching.|
|A project in maintenance mode|now, ideally to Long Term Support releases.|never|never|

## Tip

* **What** [Screen To Gif](https://www.screentogif.com/?l=zh_cn)，录制 GIF 图片的开源工具，有时候我们苦于和测试人员沟通半天还搞不清楚到底怎么复现问题，这个时候一个动图胜千言。



## Share
> [左耳朵耗子：软件开发这些年，我学会的道理和教训](https://mp.weixin.qq.com/s/-Gus3fGHXcRBvuKjrwQStA)  **学习就是逆人性的事，有些东西就是很枯燥，你就得啃，聪明点的人，啃个一两天，笨点的人需要啃个一两年，只要你啃，总有一天能啃的过去了，我觉得就是努力不要使蛮力。**
