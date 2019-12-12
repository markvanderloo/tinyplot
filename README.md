# Plotting, the tiny way


An experiment in graphics for R. Below are some preliminary thoughts. Nothing
is fixed yet.


### Close to base R

In base graphics there is very direct control over parameters including line
width, plotting characters, and so on. The idea of `tinyplot` is to keep this
direct control while also allowing for example the variable-to-aesteathics
mapping. By the way, R's `plot` function is close to having this functionality.

```r
plot(Sepal.Length ~ Sepal.Width, col=iris$Species, data=iris)
```

The vague idea is to get some of the good stuff from
[ggplot2](https://CRAN.R-project.org/package=ggplot2), while avoiding its
complexity; and also some of the good stuff from
[lattics](https://CRAN.R-project.org/package=lattice) while avoiding the large
number of parameters, and maybe learn something from [D3](d3js.org) where
applicable.



### User-focused

The idea is to borrow some ideas from Wilkinson's [grammar of
graphics](https://www.springer.com/gp/book/9780387245447), but not everything.
Wilkinson's grammar describes an object-oriented way of storing and
manipulating different components of a statistical plot. In other words: an
interface for programmers. This is reflected in direct implementations, such as
[ggplot2](https://CRAN.R-project.org/package=ggplot2). Users have to learn
about things like aesthetics mappings, layers, and geometric objects.  It
should be possible to create plots without knowing these things.

Moreover, the grammar of graphics is not the only paradigm for describing
plots. The far more powerful and successful [D3](http://www.d3js.org/)
system (Data Driven Documents) of Bostock clearly shows there are other ways to
go about these things. It is interesting to see whether the best ideas from
both worlds can be combined somehow.

### Interface

Some preliminary thoughts on interface.

- Variable-to-aesthethic mappings. Good, and user friendly.
- Adding geoms. Not so user-friendly. I'd prefer something like this
```r
tscatter(data, x=Species, y=Sepal.Length) + tline()
```
where `tscatter` and `tline` are plotting functions in their own right.

- legend outside of plot. Good. Works much better then inside the plot.


### Composability, extendability

`tinyplot` commands will yield some kind of object describing a plot. Ideally
these can be combined with a little algebra. For example, it would be nice
if we can compose different plots on a single canvas, either layered or
beside each other. 

I have no idea yet what the fundamental operations are or how this
can be presented in an intuitive interface.

### Device-independence

I have no idea how to do this, but it would be great if `tinyplot` objects
can be printed to screen, files, or web graphics.


### light-weight

[Light weight is the right weight](http://www.tinyverse.org/), especially when creating
a package. Imports will be kept at a minimum. Perhaps even at the cost of functionality:
we can't solve all problems can we?



### Hobby

This is a hobby project. So expect slow progress and breakage and it may never
finish.  For me, it is an interesting exercise going from interface design all
the way down to the technical underpinnings of a plot.



