---
title: Markdown怎么写
category:
- 教程
- 转载
tag: Markdown
---


## What is Markdown?

Markdown is a lightweight markup language. It allows people to write documents in plain text format that is easy to read and write, and supports pictures, charts, mathematical formulas, etc., and then convert them into valid HTML documents. AceMark uses [GitHub Flavored Markdown](https://github.github.com/gfm/) syntax (referred to as GFM) and supports some extended syntax. Let's get familiar with the common mark description of AceMark.

To facilitate navigation, we insert the table of content here:

[toc]

## Title

AceMark supports up to six level headings. One level heading uses one `#` at the beginning of the line, two level headings use two `##`, and so on. as follows:

```
# First level heading
## Secondary Title
### Tertiary Title
#### Level 4 heading
##### Level 5 heading
###### Level 6 heading
```


## Style

+ `**bold**` is used for **bold**
+ `*Italic*` is used to indicate *Italic*
+ `~~strikethrough~~` is used to indicate ~~strikethrough~~

## Footnote

We can insert a footnote [^footnote] here.

[^footnote]: This is the content of the footnote.

## Quote

    > This is a quote
    
effect:

> This is a quote


## Link

```
[Link title](http://www.acemark.net)
```
Output: [Link title](http://www.acemark.net)

If you want to display a network picture, the method is similar to the ordinary link, but you need to add a `!` Symbol in front.

```
![Picture title](http://www.acemark.net/img/icon.jpg)
```

![Picture title](http://www.acemark.net/img/icon.jpg)


## Table

With the following markup, you can output a table

```
| Heading 1 | Heading 2 | Heading 3 |
| ------ | ------- | ------ |
| Content 1 | Content 2 | Content 3 |
| Content 4 | Content 5 | Content 6 |
```
Output table:

| Heading 1 | Heading 2 | Heading 3 |
| ------ | ------- | ------ |
| Content 1 | Content 2 | Content 3 |
| Content 4 | Content 5 | Content 6 |


## List

### Ordered list


```
1. First item
2. Second item
```

Output results:

1. First item
2. Second item

### Unordered list

`+`, `*`, And `-` can be used to identify unordered list items. E.g:

```
+ Item 1
* Item 2
- Item 3
```

Output results:

+ Item 1
* Item 2
- Item 3


### Todo tags

```
- [ ] undone
- [X] completed
```

Output results:

- [ ] undone
- [X] completed

## Code
AceMark supports dozens of code highlighting. E.g:

### Go

    ```go
    func Fibonacci(n int) int {
        if n <= 1 {
            return n
        }
        return Fibonacci(n-1) + Fibonacci(n-2)
    }
    ```
    
Output:

```go
func Fibonacci (n int) int {
    if n <= 1 {
        return n
    }
    return Fibonacci (n-1) + Fibonacci (n-2)
}
```

### JavaScript

    ```javascript
    function Fibonacci(num) {
        if (num <= 1) return 1;
        return Fibonacci(num - 1) + Fibonacci(num - 2);
    }
    ```

Output:

```javascript
function Fibonacci (num) {
    if (num <= 1) return 1;
    return Fibonacci (num-1) + Fibonacci (num-2);
}
```

### Lua


    ```lua
    local function Fibonacci(n)
        local function doFibonacci(n, ret1, ret2)
            if (n <= 1) then
                return ret2
            end
            return doFibonacci(n - 1, ret2, ret1 + ret2)
        end
        return doFibonacci(n, 1, 1)
    end
    ```

Output:

```lua
local function Fibonacci (n)
    local function doFibonacci (n, ret1, ret2)
        if (n <= 1) then
            return ret2
        end
        return doFibonacci (n-1, ret2, ret1 + ret2)
    end
    return doFibonacci (n, 1, 1)
end
```


## Mathematical formula

AceMark supports mathematical formulas for LaTeX syntax. E.g

```
$$
f(x) = a x^2 + b x + c
$$
```

Will output a parabolic equation

$$
f(x) = a x^2 + b x + c
$$

And this expression
```
$$
F(\omega)=\int_{-\infty}^{+\infty} {f(t)e^{-i\omega t}dt}
$$
```

Will output a Fourier transform integral equation

$$
F(\omega)=\int_{-\infty}^{+\infty} {f(t)e^{-i\omega t}dt}
$$

The output matrix is ​​also very simple, just need

```
$$
\begin{bmatrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{bmatrix}
$$
```

To get the desired effect

$$
\begin{bmatrix}
1 & x & x^2 \\
1 & y & y^2 \\
1 & z & z^2 \\
\end{bmatrix}
$$

Formulas can also be displayed in-line. For example, `$f(x)=kx+b$` will output $f(x)=kx+b$, which is a straight line equation displayed in a row.
