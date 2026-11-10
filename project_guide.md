# Final Project - Deep Learning Autopilot

## 1. Overview

The rapid evolution of autonomous vehicle technology represents a paradigm shift in modern transportation, promising to drastically reduce accidents caused by human error while optimizing traffic efficiency.
Unlike traditional control systems that rely on brittle, hand-crafted rules to define driving behavior, modern autopilot systems increasingly depend on deep learning to navigate the stochastic and high-dimensional nature of real-world environments.
By leveraging architectures such as Convolutional Neural Networks (CNNs) for end-to-end learning, vehicles can move beyond simple object detection to map raw sensory inputs directly to control outputs like steering and acceleration.

This project focuses on developing a deep learning-based autopilot using behavioral cloning, enabling the model to learn and replicate safe driving trajectories from observational data.

## 2. Project Setup
> [!IMPORTANT]
> - Two students will share one BearCar hardware setup.
> - Sharing training datasets is encouraged. If a student's dataset is used by peers, the author receives an additional 5% bonus of the total project points per recipient. For example, if all 13 classmates use Student A's dataset, Student A earns a 5% * 13 = 65% bonus point addition.
> - Usage of the BearCar software are [documented](https://uca-rbeg.github.io/bearcar_docs/usage/). Please spend your time practice and get familiar.
> - It is students' responsibility to maintian the hardware. Mostly, keep the batteries charged for BearCars, gamepads and the headsets.

> [!CAUTION]
> Please please please **DISCONNECT** the BearCars' batteries before leave! 

1. [Set up](https://uca-rbeg.github.io/bearcar_docs/installation/setup_software/) [BearCar](https://github.com/UCA-RBEG/BearCar) on Raspberry Pi (and optionally on your local workstation or server).
> [!TIP]
> A dedicated computing server is available for training at IP address `192.168.0.100`.  

3. Download project repository on both the Raspberry Pi and the computing server.
```console
cd ~
git clone git@github.com:UCAEngineeringPhysics/deep-learning-autopilot-<github_username>.git ~/dl_autopilot
```

3. Link the architecture directory from the BearCar repository to your project repository.
```console
ln -s ~/BearCar/scripts/components/custom_archs ~/dl_autopilot/custom_archs
```

## 3. Requirements
### 3.1. (60%) Architecture Development.
1. Write a standalone Python script defining your model architecture class and place it in the [custom_archs/](./custom_archs/) directory for your autopilot architecture class.
Refer to the [bearnet.py](./custom_archs/bearnet.py) for an example.
2. Register your model class on both the Raspberry Pi and the server by adding `"<model_file_name>": <model_class_name>` to the `arch_registry` dictionary in [__init__.py](./custom_archs/__init__.py)   

> [!CAUTION]
> - Each student must propose a unique model architecture. Duplicate implementations or significant structural similarities to BearCar baselines or classmates' models will result in point deductions.
> - Models run on an onboard Raspberry Pi without dedicated hardware acceleration. Compute efficiency and inference speed (FPS) are critical design metrics.
 
### 3.2. (40%) Documentation & Deliverables.
  - (2%) Upload a portrait of your robot to this repository and display it in [README](README.md) with the resolution of 600 (W) x 800 (H). 
  - (15%) Upload your training dataset to the repository or provide an accessible link. Clearly declare the dataset origin (self-collected vs. shared/adapted from another student). 
  - (15%) Upload the final, demonstration-tested model file to the [models/](./models) directory.
  - (8%) In [README](./README.md) document model performance evaluated over 10 consecutive laps using the following metrics:
    1. Best lap time (pause the timer for human intervene).
    2. Average number of collisions/human interventions per lap across 10 laps.
    3. Operating speed (FPS) while autopilot is active.
> [!CAUTION]
> - Autopilot model will be retrained using the submitted dataset and proposed architecture. Ensure the uploaded dataset reliably trains a functional autopilot model.
> - Submitted model will be spot-tested on Dr. Zhang's hardware after the demonstration. If performance deviates significantly from your reported metrics, a supervised re-demo using student's hardware operated by Dr. Zhang will be required. Failing the re-demo will result in a 50% penalty on total project points and forfeiture of all bonus points.

## 4. Demonstration/Race
> [!IMPORTANT]
> - Student must demonstrate the autopilot on the track to earn the 60% Architecture Development credit.
> - Each student receives 3 official attempts. Additional attempts may be granted at the judge's discretion based on schedule and track conditions.
> - Each collision or required human intervention during a lap results in a 5% deduction from total project points.
> - Successfully catching Dr. Zhang's benchmark autopilot within 5 laps in a voluntary head-to-head race earns a 10% **bonus**.

### Demonstration Procedure
1. Position the vehicle behind the start/finish line in the Paused state (indicated by a yellow status LED).
2. The operator (holding the gamepad) must wait for the judge's verbal command before engaging autonomous mode (indicated by a purple status LED).
3. If human intervention is required, the operator must pause the vehicle before resetting it to the intervention location or following the judge's directives.
4. The operator must wait until the vehicle fully crosses the finish line before stopping or disabling the autopilot mode.

