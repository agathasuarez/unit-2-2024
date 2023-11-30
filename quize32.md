# Quiz 32

*Fig. 1.* Slide with the quiz information 

## Code
```.py
import matplotlib.pyplot as plt
from matplotlib.gridspec import GridSpec

from unit2lib import get_sensor, smoothing

import matplotlib
plt.style.use("ggplot")
matplotlib.use("MacOSX")
sensors=[]
for s in [4,5]:
    data=get_sensor(id=s)
    sensors.append(data)
    print(f"Sensor {s} obtained with {len(data)} samples")
num_samples=len(sensors[0])
average=[]
for i in range (num_samples):
    total=0
    for s in sensors:
        total += s[i]
    average.append(total/-len(sensors))
fig = plt.figure(figsize=(10,5))
grid=GridSpec(3,4,figure=fig)
plt.subplots_adjust(hspace=0.5)

box2 = fig.add_subplot(grid[0:3, 1:3])
plt.plot(average, color ="red")
plt.title("Sensor#4-Sensor#5")

box3 = fig.add_subplot(grid[1,0])
plt.plot(sensors[0], color="black")
plt.title("Sensor id=4")


box1=fig.add_subplot(grid[1,3])
plt.plot(sensors[1], color="black")
plt.title("Sensor id=5")

plt.show()

```
## Library 
```
#unit 2 lib
import requests
def get_sensor(id:int=1, ip="192.168.6.153"):
    x = requests.get(f"http://{ip}/readings")
    data = x.json()
    sensors =data["readings"][0]
    sensor=[]
    for s in sensors:
        if s ["sensor_id"]==id:
            sensor.append(s["value"])
    return sensor

def smoothing(x:list[int], size_window:int=5):
    smooth_x=[]
    t=[]
    for i in range (0, len(x), size_window):
        points=sum(x[i:i+size_window])/size_window
        smooth_x.append(points)
        t.append(i)

    return t, smooth_x
```

## Proof of work
![Screen Shot 2023-11-30 at 13 17 35](https://github.com/agathasuarez/unit-2-2024/assets/142757977/4d97caf1-0fdf-4dd9-aa1f-85c222a06f4e)

*Fig. 2.* Proof of work
