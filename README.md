# Final Project - Deep Learning Autopilot

## Background
The rapid evolution of autonomous vehicle technology represents a paradigm shift in modern transportation, promising to drastically reduce accidents caused by human error while optimizing traffic efficiency. 
Unlike traditional control systems that rely on brittle, hand-crafted rules to define driving behavior, modern autopilot systems increasingly depend on deep learning to navigate the stochastic and high-dimensional nature of real-world environments. 
By leveraging architectures such as Convolutional Neural Networks (CNNs) for end-to-end learning, vehicles can move beyond simple object detection to map raw sensory inputs directly to control outputs like steering and acceleration. 
This project focuses on developing such a deep learning-based autopilot, aiming to implement a behavioral cloning approach that allows the model to learn and replicate safe driving trajectories from observational data.

## [BearCar](https://github.com/UCAEngineeringPhysics/BearCar) Setup
Please follow the guides in BearCar's [documentation](https://ucaengineeringphysics.github.io/bearcar_docs/) to set up your racing robot.

> [!TIP]
> Start project setup over if necessary.
> Back up important data, then `rm -rf ~/BearCar` will wipe the project out from either Raspberry Pi or server. 

## Requirements
- Use `(180, 200, 3)` as your autopilot's input image size.
  - Width: 180
  - Height: 200
  - Color channels: 3  
- Develope the architecture of the deep learning model, save it and upload it to [model_architecture.py](model_architecture.py).
> [!WARN]
> Your model architecture cannot be identical to the one used by the BearCar or by the other teams. 

- (Optional) Feel free to [fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo) the [BearCar](https://github.com/UCAEngineeringPhysics/BearCar) repository. Make changes and submit [pull requestes](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) if you've developed new features or corrected mistakes.
> [!TIP]
> Extra points will be rewarded to the person or team who submitted the **accepted** PR.
  

## Final Race Rubric 
- **(100%) The deployed autopilot is expected to finish at least one lap of the track autonomously.** Any human correction/interference will cost 5% of the total score.
- For the final demonstration, set and start the BearCart at the "Start/Finish Line".
- Release the autopilot after the instructor's verbal cue.
- Operators may follow and correct the robot if any unexpected situation (crash, stuck, off-track, etc.) happened. Be familiar with the `PAUSE` button.
- The time cost to finish a lap and the number of human corrections/interferences will be recorded.
- Each team has 5 attempts. Each attempt should not last over 2 minutes.
- The autopilot model will be tested and showcased on the track as shown below.
![race_track](111_raceway.png)
