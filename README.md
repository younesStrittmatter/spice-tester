# Name-Of-Your-Contribution (don't include AutoRA here)

Explain what your contribution is doing here

You can include inline mathematics like this: \(3 < 4\)

Include block mathematics like this (don't forget the empty lines above and below the block):

$$  
y + 1 = 4 
$$

... or this:

\[
E(\mathbf{v}, \mathbf{h}) = -\sum_{i,j}w_{ij}v_i h_j - \sum_i b_i v_i - \sum_j c_j h_j
\]

... or this:

\begin{align}
    p(v_i=1|\mathbf{h}) & = \sigma\left(\sum_j w_{ij}h_j + b_i\right) \\
    p(h_j=1|\mathbf{v}) & = \sigma\left(\sum_i w_{ij}v_i + c_j\right)
\end{align}


Include inline mathematics like this \(x < 1\) or this $c = 3$ or this
or block mathematics:

\[
x + 1 = 3
\]




# Quickstart Guide

You will need:

- `python` 3.8 or greater: [https://www.python.org/downloads/](https://www.python.org/downloads/)

*Your-contribution* is a part of the `autora` package:

```shell
pip install -U autora["your-contribution"]
```


Check your installation by running:
```shell
python -c "from autora.your_contribution import something"
```
