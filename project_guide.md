# Final Project - Deep Learning Autopilot

## 1. Overview

The rapid evolution of autonomous vehicle technology represents a paradigm shift in modern transportation, promising to drastically reduce accidents caused by human error while optimizing traffic efficiency.
Unlike traditional control systems that rely on brittle, hand-crafted rules to define driving behavior, modern autopilot systems increasingly depend on deep learning to navigate the stochastic and high-dimensional nature of real-world environments.
By leveraging architectures such as Convolutional Neural Networks (CNNs) for end-to-end learning, vehicles can move beyond simple object detection to map raw sensory inputs directly to control outputs like steering and acceleration.

This project focuses on developing such a deep learning-based autopilot, aiming to implement a behavioral cloning approach that allows the model to learn and replicate safe driving trajectories from observational data.

## 2. Project Setup
> [!IMPORTANT]
> - Two students will share one BearCar hardware.
> - Sharing the training data is allowed.
If a student's dataset get shared once, he/she will be awarded with an extra 5% of the project's total points.
Which means, if the entire class (14) use the same dataset collected by student A, then student A will be awarded an extra ($5\% \times 13 = 65\%$) points for the contribution. 

1. Set up [BearCar](https://uca-rbeg.github.io/bearcar_docs/) on Raspberry Pi (and optionally on server computer).
> [!TIP]
> A computing server will be set up for your convenience with the ip address: `192.168.0.100`.  

3. Download project repository on both Raspberry Pi and server computer.
```console
cd ~
git clone git@github.com:UCAEngineeringPhysics/deep-learning-autopilot-<github_username>.git ~/dl_autopilot
```

3. Link the autopilot architecture directory from BearCar repository to this repository.
```console
ln -s ~/BearCar/scripts/components/custom_archs ~/dl_autopilot/custom_archs
```

## 3. Requirements
1. (60%) Develop a unique autopilot architecture.
    1. Use a standalone Python script and upload it to the [custom_archs/](./custom_archs/) directory for your autopilot architecture class.
    Refer to the [bearnet.py](./custom_archs/bearnet.py) for an example.
    2. Register your architecture (on both Raspberry Pi and server) in the [__init__.py](./custom_archs/__init__.py) by adding `"<model_file_name>": <model_class_name>` to the `arch_registry` dictionary.  

> [!CAUTION]
> - Each individual needs to propose a unique model architecture (can't be the same as the ones used by BearCar nor as anyone else's). Points may be taken out due to the high similarity to an existing architecture.
> - Bear in mind that the model will be running on a Raspberry Pi without any hardware acceleration. Your model's inference speed is a big concern of this project. 
 
2. (40%) Documentation.
  - (15%) Share your training dataset by uploading it to this repository or sharing the link for accessing it.
Declare the source (collected by someone or by yourself) of your dataset. 
  - (15%) Upload the race proofed autopilot model to the [models/](./models/) directory.
  - (10%) Document your autopilot's performance in [README](./README.md) with the following 3 metrics:
    1. Average lap time in 10 laps.
    2. Number of collisions/human intervene per lap in 10 laps.
    3. Frame rate when autopilot is on duty.
> [!CAUTION]
> - An autopilot model will be trained using the uploaded dataset and the proposed architecture. Please make sure the dataset will lead to a successful training and a reasonable autopilot.
> - Model will be tested using Dr. Zhang's hardware after the "race". If the model performed completely different from the demonstration, a re-race will be called using student's hardware operated by Dr. Zhang. Failed to "re-race" will cost a 50% loss of the total points and disqualification of all the bonus points.


## 4. Demonstration/Race
> [!IMPORTANT]
> - Everyone needs to demonstrate his/her autopilot on the track to redeem the architecture development credits (60%).
> - Each teammember has **3 attempts** in total. Extra attempts may given based on the time and the actual conditions.
> - Every collision, and human interference in one lap will lead the autopilot's owner losing 5% of total points.
> - If a student's autopilot can Catch Dr. Zhang's autopilot within 5 laps in a voluntary race, 10% bonus will be given.

### Demonstration Procedure
1. Set the robot behind the start/finish line under the "Paused" status (yellow light on).
2. Operator (who has the gamepad) needs to wait the judge's verbal order to start the autopilot (purple light will be turned on).
3. If human intervene is needed, operator has to pause the robot before reset the robot to where it was paused or follow the judge's order.
4. Operator has to wait the robot crossed the finish line to disable the robot.

