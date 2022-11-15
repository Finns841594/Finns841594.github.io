---
layout: post
title:  "Review for CS50 Course - Python & C"
date:   2022-09-05 20:00:00 +0200
categories: CS50
---

## 0

From week 1 to week 5, the course is talking about how you program in C, and at the same time learning the basic knowledge about hou computer works. Then at the week 6, its about doing the same thing again but by a higer level language which is Python.

## 1 Basics: Data types, conditions, loops

1. [This](https://en.wikipedia.org/wiki/C_data_types#:~:text=Basic%20types-,Main%20types,of%20storage%20size%2Dspecific%20declarations.) page explains clearly the data types in C. But a good take away will be the follows:

- bool: In C, you have bool value start with lower-case `true` and `false`, while in Python it starts with Upper-case `True` and `False`. And `false` equals to `0`.
- char: No string in C, only char*. 
- double & float: float takes 4 bytes whereas double takes 8 bytes (thats the reason why it called "double"?), so double has the higer percision.
- int: most similar to "number" in our the natural language. And I prefer to use 1 and 0 to substitue `true` and `false`.
- long: like float and double, long is the int-type data but takes more space in the memory.

2. I like how it works in C to use conditions:

```C
if (a < b)
    {
        printf("a is smaller than b.\n");
    }
else if (a > b)
    {
        printf("a is bigger than b.\n");
    }
```

3. But the loops are little cumbersome:

```C
for (int i = 0; i < 3; i++)
{
    printf("meow\n");
}
```
You need to basically write this several times in every program you write.


## 2 Algorithms


## 3 Memory


## 4 Data Structures


## 4 Python




