+++
date = '2025-01-22T16:00:20+08:00'
draft = true
title = 'Hello'
math = true
+++

## Introduction

This is **bold** text, and this is *emphasized* text.

Visit the [Hugo](https://gohugo.io) website!

## Emoji

To enable emoji, set `enableEmoji` to `Enable` in site's configuration 
and then type emoji directly in content.

🥰 😁

## Math Typesetting

Backwards of a function that multiplies a matrix with a row vector and take a relu.

$$
f(x, y) = \text{relu}(x_{j, i} \times y_j)\text{ for } i = 1\ldots N_0,\ j = 1\ldots N_1
$$

## Code Highlight 

```cpp
#include <iostream>
#include <foramt>

int main() {
    std::cout << std::format("Hello World!\n);
    return 0;
}

```