# Mod

Description: Just a simple modulo challenge

My approach: The source code was given to us, so first I had to understand how it worked. The code first generated a random number (= x). Then it asked for an input (= y), and outputted y%x. If we guess x correctly just by knowing y%x, the flag is unlocked. The trick was hidden in the property of modulo in Python.
In Python, the modulo operator works such that:
```python
a%b = a - (a//b)*b
```
where a//b is the floor function (i.e. -5/3 = -2)  
So, if we input y such that we can find x from y%x, we can solve the problem. Notice that (-1)//x = -1 for all integers x>0. So, if we take y = -1,  
(-1)%x = (-1) - (-1)*x.  
Therefore x = 1 + (-1)%x  
where we know (-1)%x (the output given by the server)  

  
Summary:  
We need to input (-1)  
We get an output (= k)  
We input (k + 1)  
The server returns the flag, which is scriptCTF{-1_f0r_7h3_w1n_4a3f7db1}
