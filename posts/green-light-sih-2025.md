# Green Light: adaptive traffic signals for Smart India Hackathon 2025

## The project

Green Light is an adaptive traffic-signal system. Team Void Pointers, six students from DBS Global University, built it for Smart India Hackathon 2025 and reached the national finals at IIIT Dharwad. I was the primary presenter. I built the frontend and the SUMO simulations.

## How it works

The final code is about 3,400 lines of Python. It detects vehicles in camera feeds with a YOLO model, tracks them with an IoU matcher and a Kalman filter, and passes the result to a decision engine and a risk evaluator. The evaluator weighs five behaviours: gap insertion, side cutting, wrong-way driving, red-light jumping and speeding. It then recommends extending the green phase, raising an alert or an emergency stop. The system also has emergency-vehicle detection, a FastAPI server with one engine per camera, a threaded multi-camera manager and a WebSocket viewer. The code includes the SUMO network, routes, detectors and signal plan.

## The detector

I trained a YOLOv5l model for 50 epochs at 640 px on the India Driving Dataset, with 31,569 training and 10,225 validation images and 15 classes, including autorickshaws and riders. The last of three training runs reached precision 0.78, recall 0.35 and mAP@0.5 of 0.40 on validation.

## The four hours before the demo

With about four hours left, the team's work was falling apart. My mentor asked me to build a SUMO simulation that showed the team's model. I had never used SUMO and knew only basic terminal commands. I read up on the commands that control SUMO, got it running, and it worked well. My professor was proud of it.

## Where the code is

The final code is not in a public repository yet.
