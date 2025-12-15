# Context-Aware Hybrid Object Detection for Autonomous Vehicle Perception

This project runs a **hybrid perception pipeline** where a Jetson device can run:
- **Local YOLO11n** (always available), and
- **Remote YOLO11x** on an **A6000 server**, reached through a **Windows relay** (simulation bridge).

The Jetson decides per-frame whether to use cloud or local based on:
- network availability (Jetson ↔ Windows),
- a CNN scene classifier (simple vs complex),
- a max paerception latency allowed budget using an estimated direct latency model.

More information about the project or required software can be found [here: ](https://jeankwon.github.io/ECM202A_2025Fall_Project_8/)

Make sure to check the port and IP address of your set up and update the corresponding fields in the script. 
frames directory have some example jepg images that can be used. 

On the A6000 machine, run:
```
python yolo_server.py
```
On your Windows device for relay, run:

```
ssh -L 5001:localhost:5001 yourname@ASERVER_IP
```
On the other terminal of Window, run: 
```
python relay_server.py
```

Lastly, on your Jetson, run:
```
python test.py

---




