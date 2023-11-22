# Quiz 21
![Screen Shot 2023-11-22 at 17 34 36](https://github.com/agathasuarez/unit-2-2024/assets/142757977/76be33a4-9d2b-45ed-a87d-51393bf04b20)

*Fig. 1.* Slide with the quiz information 

## Code
```.py
def produce (n:int, m:int, s:int):
    x_out = []
    y_out= []
    for _ in range (n):
        x = random.randint (0,100)
        y = x**(0.5*((m/s)**2))
        x_out.append(x)
        y_out.append(y)
    return y_out, x_out

plt.style.use('ggplot')
y, x = produce (n=10, m=5, s=2)
plt.plot (x, y,color='r',marker='+')
plt.xlabel ("x", fontsize=20)
plt.xlabel ("$y=x^{(1/2)(m/s)}$", fontsize=20)
plt.show()
```
## Proof of work
![Screen Shot 2023-11-22 at 17 41 05](https://github.com/agathasuarez/unit-2-2024/assets/142757977/ee688c3e-dade-4c8e-a8b5-b02b7aa3775c)

*Fig. 2.* Proof of work
