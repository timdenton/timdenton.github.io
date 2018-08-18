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


np.random.seed(11)  # placing a seed, makes 'random' return the same values
fc = np.random.uniform(low=-10.0, high=10.0, size=(20))
fc
```

This will return an array of type `numpy.ndarray`:

```
array([-6.39460622, -9.61049517, -0.73562947,  4.49867858, -1.59592791,
       -0.29145804, -9.74438371, -0.25256785,  8.83613305,  7.01590179,
        4.5992894 , -7.82527856,  7.87808341,  7.14308494, -6.69826765,
        2.64668028, -9.59032774, -7.66525462, -3.67265377, -6.84175387])
```

We can now select only those elements of `fc` that are > 4. For this we first create another NumPy array of boolean values:

```python
greater4 = abs(fc) > 4
greater4
```

```
array([ True,  True, False,  True, False, False,  True, False,  True,
        True,  True,  True,  True,  True,  True, False,  True,  True,
       False,  True])
```

Applying this True/False mask to `fc` will return only those numbers of `fc` that are > 4, again of type `numpy.ndarray`:

```python
fc[greater4]
```

```
array([-6.39460622, -9.61049517,  4.49867858, -9.74438371,  8.83613305,
        7.01590179,  4.5992894 , -7.82527856,  7.87808341,  7.14308494,
       -6.69826765, -9.59032774, -7.66525462, -6.84175387])
```

Of course the following will return the same array:

```python
fc[abs(fc) > 4]
```

```
array([-6.39460622, -9.61049517,  4.49867858, -9.74438371,  8.83613305,
        7.01590179,  4.5992894 , -7.82527856,  7.87808341,  7.14308494,
       -6.69826765, -9.59032774, -7.66525462, -6.84175387])
```

