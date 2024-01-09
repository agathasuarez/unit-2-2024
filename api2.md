#api2
import requests

user={"username":"agatha", "password":"kk1863"}
ip="192.168.6.153"

#request_user
answer=requests.post(f"http://{ip}/register", json=user)
print(answer.json())

answer = requests.post(f"http://{ip}/login", json=user)
print(answer.json())

cookie=answer.json()["access_token"]
sensor_a={"type":"Temperature", "location":"R1-15", "name":"agatha", "unit": "C"}
header={"Authorization":f"Bearer {cookie}"}
answer=requests.post(f"http://{ip}/sensor/new", json=sensor_a, headers=header)
print(answer.json())
record={"sensor_id":19, "value":30}
answer=requests.get(f"http://{ip}/user/readings", json=record, headers=header)
print(answer.json())
#get all my recordings
print (answer.json())
