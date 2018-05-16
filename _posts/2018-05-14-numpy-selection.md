---

layout: post
title: Selection with NumPy Arrays
author: Tim

---

Selecting or filtering Python lists is very tedious. With NumPy arrays, this is very easy.

Here, I show you an example using a random list of fold-change data, e.g. from a gene expression analysis.

Let's create random array of 20 floating point numbers ranging from -10 to +10 using the NumPy's random module:

```python
import numpy as np

fc = np.random.uniform(low=-10, high=10, size=(20))
print(fc)
```

This will return an array of type `numpy.ndarray`:

```
[-2.76125903 -7.55415264  6.91925317 -6.44594408  6.05675712 -0.55402255
  9.92516181  5.66616252  4.43385296  5.44506948  7.14491155  4.46466178
 -2.40165222  1.1747153   6.01604013 -2.22270074  0.32039262  7.86113264
 -4.2706525   5.05908863]
```

We can now select only those elements of `fc` that are >= 2. For this we first create another NumPy array of boolean values:

```python
high = abs(fc) >= 2
print(high)
```

```
array([ True,  True,  True,  True,  True, False,  True,  True,  True,
        True, False,  True,  True,  True, False,  True, False, False,
        True,  True])
```

