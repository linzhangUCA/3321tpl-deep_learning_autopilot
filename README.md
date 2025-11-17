# Final Project - Deep Learning Autopilot

## Background

The rapid evolution of autonomous vehicle technology represents a paradigm shift in modern transportation, promising to drastically reduce accidents caused by human error while optimizing traffic efficiency.
Unlike traditional control systems that rely on brittle, hand-crafted rules to define driving behavior, modern autopilot systems increasingly depend on deep learning to navigate the stochastic and high-dimensional nature of real-world environments.
By leveraging architectures such as Convolutional Neural Networks (CNNs) for end-to-end learning, vehicles can move beyond simple object detection to map raw sensory inputs directly to control outputs like steering and acceleration.
This project focuses on developing such a deep learning-based autopilot, aiming to implement a behavioral cloning approach that allows the model to learn and replicate safe driving trajectories from observational data.

## Project Setup

1. Please follow the guides in BearCar's [documentation](https://ucaengineeringphysics.github.io/bearcar_docs/) to download and set up [BearCar](https://github.com/UCAEngineeringPhysics/BearCar) on both Raspberry Pi and server computer.

> [!TIP]
> Start over project setup if necessary.
> Back up important files, then `rm -rf ~/BearCar` will wipe the project out from either Raspberry Pi or server.

2. Download project repository on both Raspberry Pi and server computer.

```console
cd ~
git clone git@github.com:UCAEngineeringPhysics/deep-learning-autopilot-<team_name>.git ~/dl_autopilot
```

> [!NOTE]
>
> - You need to substitute `<team_name>` with your actual team team.
> - The downloaded project repository will be saved as `~/dl_autopilot/`.

3. Use `(width=180, height=200, color_channel=3)` as your autopilot's input image size.
This requires a little modification of the **BearCar** scripts on the **Raspberry Pi**.

- Modify image resolution on line 37 in [teleop.py](https://github.com/UCAEngineeringPhysics/BearCar/blob/scripts/teleop.py).
- Modify image resolution on line 43 in [autopilot.py](https://github.com/UCAEngineeringPhysics/BearCar/blob/scripts/autopilot.py).

4. Modify model source to use models develop by your teammembers.
This requires modification of the **BearCar**'s scripts on both **Raspberry Pi** and **server**.

- Link the autopilot architecture directory from this project repository to BearCar repository.

```console
ln -s ~/dl_autopilot/autopilot_architectures ~/BearCar/scripts/autopilot_architectures
```

- Modify line 11 and line 23 in [autopilot.py](https://github.com/UCAEngineeringPhysics/BearCar/blob/scripts/autopilot.py) to import and deploy desired model, for example:

```python
# ...
from autopilot_architectures.dummy_model import DummyPilotNet  # line 11: from autopilot_architectures.model_file_name import ModelClassName
# ...
model = DummyPilotNet()  # line 23
# ...
```

- Modify line 11, and line 145 in [learn.py](https://github.com/UCAEngineeringPhysics/BearCar/blob/scripts/learn.py) to import and use desired model

```python
# ...
from autopilot_architectures.dummy_model import DummyPilotNet  # line 11
# ...
model = DummyPilotNet().to(DEVICE)  # line 145
# ...
```

## Requirements

- Design and develop the architecture of the deep learning autopilot.
Save all teammember's model files in [autopilot_architectures/](autopilot_architectures/) directory with distinguished and identifiable names.
For example: [autopilot_architectures/dummy_model.py](autopilot_architectures/dummy_model.py)

> [!CAUTION]
>
> - Each teammember needs to propose a unique model architecture (can't be the same as BearNet nor as anyone else's).
> - No credits will be given to teammembers who failed to upload the model architecture.

- (Optional) Feel free to [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) and customize the [BearCar](https://github.com/UCAEngineeringPhysics/BearCar) repository. Submit [pull requestes](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) if you've developed new features or corrected mistakes.

> [!TIP]
> Extra points will be rewarded to the person or teams who submitted the **accepted** PR.
  
## Race Rules

### Rules

1. Set the robot behind the "Start/Finish" line with "Paused" status (yellow light on).
2. Operator in the team needs to Please wait the judge's verbal order to start the autopilot (
**(100%) The deployed autopilot is expected to finish at least one lap of the track autonomously.**

- Any human correction/interference will **cost 5%** of the total score.
- An extra
- set and start the robot at the "Start/Finish Line".
- Release the autopilot after the instructor's verbal cue.
- Operators may follow and correct the robot if any unexpected situation (crash, stuck, off-track, etc.) happened. Be familiar with the `PAUSE` button.
- The time cost to finish a lap and the number of human corrections/interferences will be recorded.
- Each team has 5 attempts. Each attempt should not last over 2 minutes.
- The autopilot model will be tested and showcased on the track as shown below.
-

![race_track](race_track.jpg)
