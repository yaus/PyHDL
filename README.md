# PyHDL
Using python to do HDL

"""
from PyHDL import Module, IO

class DFF(Module):
  clk = IO.input()
  rst_n = IO.input()
  d = IO.input()
  q = IO.output()
  
  @Edge(clk.rise, rst_n.fall)
  def flop(self):
   
"""
