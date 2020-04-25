# PyHDL
Using python to do HDL

# D-FlipFlop
```python
from PyHDL import Module, IO

class DFF(Module):
  clk = IO.input()
  rst_n = IO.input()
  d = IO.input()
  q = IO.output()
  
  @edge(clk.rise, rst_n.fall)
  def flop():
    if ~rst_n.value:
      q.assign = 0
    else:
      q.assign = d
```

# MUX
```python
from PyHDL import Module, IO, Parameter

class MUX(Module):
  width = Parameter(8)
  A = IO.input(width)
  B = IO.input(width)
  S = IO.input()
  O = IO.output(width)
  
  @sense(A,B,S)
  def sel():
    if S.value:
      O.assign = B
     else:
      O.assign = A
```

 # Instantiation
 ```python
 from PyHDL import Module, IO, Parameter
 
 class PIPE(Module):
  width = Parameter(8)
  clk = IO.input()
  rst_n = IO.input()
  D = IO.input(width)
  Q = IO.output(width)
  
  dff = [DFF( clk=clk.connect,
              rst_n=rst_n.connect,
              d=D[i].connect,
              q=Q[i].conenct) for i in range(8)]
```

# Instatiation
```python
 from PyHDL import Module, IO, Parameter
 
 class PIPE(Module):
  width = Parameter(8)
  clk = IO.input()
  rst_n = IO.input()
  D = IO.input(width)
  Q = IO.output(width)
  
  dff = [DFF( clk=clk.connect,
              rst_n=rst_n.connect,
              d=D[i].connect,
              q=Q[i].conenct) for i in range(8)]
```
