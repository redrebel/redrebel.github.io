---
layout: post
published: true
title: How to Sort - C# 
date: '2019-10-19'
tags: [C#, sort]
---

```c#
int[] arr = {1, 4, 3, 2};
List<int> list = arr.ToList();

Console.WriteLine(list);

list.Sort(delegate(int a, int b){
  return b.CompareTo(a);  // 내림차순
});

Console.WriteLine(list);
```

