# Offline Smart Doorbell

EC-ENG 535/635 (Fall 2026) course project

## Motivation
Most smart doorbells send video to the cloud, which costs money, adds latency, and raises privacy concerns. We want a doorbell that does all of its recognition on a small edge device, so nothing leaves the house and it still works without internet.

## Design Goals
- Run person/face detection and recognition fully on a Raspberry Pi
- Keep models small enough to run in near real time on the Pi
- Tell apart known people (household members) from unknown visitors
- Log or alert when someone shows up
- Stretch: detect delivery workers (package/pizza)

## Deliverables
- Lightweight person/face detection model deployed with TensorFlow Lite
- Embedding-based recognition: compute embeddings for known people, store them, and match new faces against them
- Pipeline that captures an image when someone appears and runs inference on the device
- Optional alert (phone notification or log file)
- Optional delivery person detection
- Code and a live demo running directly on the Pi
- Final report

## System Blocks
1. Camera module captures frames
2. Person/face detector finds and crops faces
3. CNN produces an embedding for each face
4. Matcher compares against stored embeddings of known people
5. Decision logic labels the visitor (known, unknown, delivery)
6. Alert/logging output

## Hardware / Software
Hardware: Raspberry Pi, Pi camera module, (optional) speaker or LED for alerts
Software: Python, TensorFlow Lite, OpenCV, Google Colab for any training or fine-tuning

## Team Responsibilities
- Setup (Pi, camera, OS, dependencies): Sahil
- Software (main pipeline and integration): Nikhil, Hanosh
- Networking (alerts/notifications): Nikhil, Sahil
- Writing (README, report, documentation): Hanosh
- Research (models, datasets, papers): Hanosh
- Algorithm design (detection and embedding matching, evaluation): Nikhil, Sahil

## Timeline
- Week 1: Set up repo, get Pi and camera working, finish literature review
- Week 2: Get a detection model running on the Pi, measure speed
- Week 3: Add embedding extraction and matching for known faces
- Week 4: Build the full capture to inference to decision pipeline
- Week 5: Add alerts and the delivery person feature, test accuracy and latency
- Week 6: Optimize models, collect results, prep demo
- Final: Demo and report

## References
- Howard et al., MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications, https://arxiv.org/abs/1704.04861
- Schroff et al., FaceNet: A Unified Embedding for Face Recognition and Clustering, 2015
- TensorFlow Lite documentation, https://www.tensorflow.org/lite
