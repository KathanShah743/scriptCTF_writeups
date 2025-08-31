# scriptCTF_writeups

# 1. Subtract
Description: The image size is 500x500. You might want to remove some stuff...

My approach:
There was a zip file given to us that contained a .txt file with some coordinates. The image size is given 500x500, which must be of some use. Notice that the maximum possible number of unique coordinates are 500x500=250000 whereas the number of coordinates given to us is 250573. Hence there must be some points that are repeated (by pigeon-hole principle). The first thought that came to mind was to plot all points occuring exactly once, but the number of coordinates would be too high. The natural next thought was to plot all points occuring more than once, which I did using the python code shown below. The code takes the coordinates as input, and if they are already present (i.e. the coordinates are repeated), it stores them in a different array. Plotting these repeated points yields the flag: scriptCTF{5ub7r4c7_7h3_n01s3}

```python
import matplotlib.pyplot as plt
import numpy as np
xpoints = np.array([])
ypoints = np.array([])
xpointsrepeated = np.array([])
ypointsrepeated = np.array([])
with open('coordinates.txt','r') as file:
    lines = file.readlines()
for line in lines:
    coord = line.strip()
    x,y = coord.split()
    intx,inty = int(x[1:-1]),int(y[:-1])
    for j in range(len(xpoints)):
        if intx==xpoints[j] and inty==ypoints[j]:
            xpoints,ypoints = np.delete(xpoints,j),np.delete(ypoints,j)
            xpointsrepeated,ypointsrepeated = np.append(xpointsrepeated,intx),np.append(ypointsrepeated,inty)
            break
    xpoints,ypoints = np.append(xpoints,intx),np.append(ypoints,inty)
for i in range(len(xpointsrepeated)):
    print(xpointsrepeated[i],ypointsrepeated[i])
plt.plot(xpointsrepeated,ypointsrepeated,'o')
plt.show()
```

The text is better visible after plotting the points in Desmos, which is shown below:

![subtract_flag](subtract_flag.png)
