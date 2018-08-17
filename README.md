# Rectangular Linear Assignment Problem - Jonker-Volgenant Solver (rlapjv)


## About
This is a fork of lapjv project (https://github.com/src-d/lapjv) to extend JV solver to rectangular matrix (2d numpy array).  Instead of transforming the rectangular matrix to a square matrix, the rlapjv is to extend the lapjv algorithm in the algorithmic level (*rlap.h*). Thanks to AVX accelaration (credit to the original lapjv), the rlapjv is incredibly efficient.  The square-to-rectangular extension is based on the paper:
> Bijsterbosch, J. & Volgenant, A. Solving the Rectangular assignment problem and applications. Ann Oper Res (2010) 181: 443 https://doi.org/10.1007/s10479-010-0757-3. 

Compared with the lapjv solver, two first initialization steps in lapjv are discarded, since the dual variables $v$ (price) are no longer unbounded ($v$ is less than or equal to zero). In this paper, several enhancements are described, but this package does not implement any but is a simple extension directly from lapjv. The enhancement will be the to-dos as well as the $k$-cardinality derivative of linear assignment problem. 

## Installation and Usage
Virtual environment is recommended for this dev python package. Here is an example of installation based on conda environment.
```bash
$ conda create --name rlap
$ source activate rlap
$ python setup.py install
```

To use the rlap is similar to lapjv. Here is a simple example.
```python
import numpy as np
from rlapjv import rlapjv
dim0, dim1 = 800, 1000
costs = np.random.rand(dim0, dim1)
rind, cind, sumcost, u_price, v_price = rlapjv(costs)
```

## To-Do
   1. $\beta$-best enhancement in augmenting row reduction initialization
   2. heap-based todo split enhancement in shortest augmenting path
   3. algorithmic $k$-cardinality extension based on transformation
