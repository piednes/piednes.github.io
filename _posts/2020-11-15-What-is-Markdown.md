---
title: Markdown怎么写（附jekyll官方文档）
category:
- 教程
- 转载
tag: Markdown
link: http://jekyllcn.com/docs/home/
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

```附：公式使用```
One of the rewards of switching my website to [Jekyll](http://jekyllrb.com/) is the
ability to support **MathJax**, which means I can write LaTeX-like equations that get
nicely displayed in a web browser, like this one \\( \sqrt{\frac{n!}{k!(n-k)!}} \\) or
this one \\( x^2 + y^2 = r^2 \\).

<!--more-->

<img class="centered" src="https://www.mathjax.org/badge/mj-logo.svg" />

### What's MathJax?

If you check MathJax website [(www.mathjax.org)](http://www.mathjax.org/) you'll see
that it *is an open source JavaScript display engine for mathematics that works in all
browsers*.


### How to implement MathJax with Jekyll

I followed the instructions described by Dason Kurkiewicz for
[using Jekyll and Mathjax](http://dasonk.github.io/blog/2012/10/09/Using-Jekyll-and-Mathjax/).

Here are some important details. I had to modify the Ruby library for Markdown in
my ```_config.yml``` file. Now I'm using redcarpet so the corresponding line in the
configuration file is: ```markdown: redcarpet```

To load the MathJax javascript, I added the following lines in my layout ```post.html```
(located in my folder ```_layouts```)

{% highlight r %}
<script type="text/javascript"
    src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
{% endhighlight %}

Of course you can choose a different file location in your jekyll layouts.

Note that by default, the **tex2jax** preprocessor defines the
LaTeX math delimiters, which are ```\\(...\\)``` for in-line math, and ```\\[...\\]``` for
displayed equations. It also defines the TeX delimiters ```$$...$$``` for displayed
equations, but it does not define ```$...$``` as in-line math delimiters. To enable in-line math delimiter with ```$...$```, please use the following configuration:

{% highlight r %}
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    processEscapes: true
  }
});
</script>
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
{% endhighlight %}


### A Couple of Examples

Here's a short list of examples. To know more about the details behind MathJax, you can
always checked the provided documentation available at
[http://docs.mathjax.org/en/latest/](http://docs.mathjax.org/en/latest/)

Let's try a first example. Here's a dummy equation:

$$a^2 + b^2 = c^2$$

How do you write such expression? Very simple: using **double dollar** signs

{% highlight r %}
$$a^2 + b^2 = c^2$$
{% endhighlight %}

To display inline math use ```\\( ... \\)``` like this ```\\( sin(x^2) \\)``` which gets
rendered as \\( sin(x^2) \\)


Here's another example using type ```\mathsf```

{% highlight r %}
$$ \mathsf{Data = PCs} \times \mathsf{Loadings} $$
{% endhighlight %}

which gets displayed as

$$ \mathsf{Data = PCs} \times \mathsf{Loadings} $$

Or even better:

{% highlight r %}
\\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]
{% endhighlight %}

is displayed as

\\[ \mathbf{X} = \mathbf{Z} \mathbf{P^\mathsf{T}} \\]

If you want to use subscripts like this \\( \mathbf{X}\_{n,p} \\) you need to scape the
underscores with a backslash like so ``` \mathbf{X}\_{n,p} ```:

{% highlight r %}
$$ \mathbf{X}\_{n,p} = \mathbf{A}\_{n,k} \mathbf{B}\_{k,p} $$
{% endhighlight %}

will be displayed as

\\[ \mathbf{X}\_{n,p} = \mathbf{A}\_{n,k} \mathbf{B}\_{k,p} \\]
