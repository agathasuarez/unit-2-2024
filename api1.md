import requests
import matplotlib.pyplot as plt
ip_server ="192.168.6.153"
data=requests.get(f'http://{ip_server}/readings')
data = data.json()
x = data ['readings'][0]
print(f"There are {len(x)} records in the server")
my_sensors = {1:[],2:[]}
for record in x:
    id_sensor=record['sensor_id']
    if id_sensor in my_sensors:
        value=record['value']
        my_sensors[id_sensor].append(value)
print (my_sensors)

fig=plt.Figure(figsize=(10,8))
plt.subplot(2, 1, 1)
plt.title("Sensor outside")
plt.plot(my_sensors[1], color="red")
plt.subplot(2,1,2)
plt.title("Sensor inside")
plt.plot(my_sensors[2], color="black")
plt.show()
