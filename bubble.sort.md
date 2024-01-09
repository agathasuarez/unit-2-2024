x=[5,6,3,2,1,4]
noChange=True
while noChange:
    for i in range (len(x)-1):
        if x [i]>x[i+1]:
            temp=x[i]
            x[i]=x[i+1]
            x[i+1]=temp
            noChange=True
print(x)
