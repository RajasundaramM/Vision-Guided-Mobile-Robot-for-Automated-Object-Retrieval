# Vision-Guided-Mobile-Robot-for-Automated-Object-Retrieval
I developed a mobile robotic system capable of autonomously navigating an arena and relocating scattered objects to their designated places. While the arena in this project is a restricted and obstacle-free zone, and the objects are classified based on color, further advancements can be done for developing a bot effective in domains such as warehouse inventory management, housekeeping etc..
<p align="center">
  <a href="https://youtube.com/shorts/S0XBqufj1W8" target="_blank">
    <img src="Demo_gif.gif" alt="Sorting in Action" width="600"/>
  </a>
</p>

## Hardware setup
- The arena mentioned is a rectangular zone. Checkerboards are placed on all corners of the arena for extrinsic camera calibration. 
- Color cubes of 3 different colors are the target objects that are scattered across the arena. Circular color charts of 3 different colors are placed in the arena which are treated as platforms where the cubes are to be placed. 
- The arena is monitored from a top-down view using Arducam that is interfaced with Raspberry Pi 5. 
- A modified Propeller-boebot with a 2-DOF gripper at the front is used as the mobile manipulator for sorting the cubes. 
- The Raspberry Pi 5 runs object detection, localisation, path planning, and control algorithms and sends the control commands to boebot via bluetooth. The boebot receives those commands and handles lower-level controls of the continuous servo motors to realise control of the bot's heading.

## Camera Calibration
One-time estimation of the intrinsic camera parameters is done by capturing multiple pics of a checkerboard at various distances and angles relative to the camera. These images are fed to the MATLAB's camera calibration toolbox to estimate the intrinsic parameters. Since the camera's position and orientation relative to the arena could change between trials, the extrinsic parameters are estimated every time the localisation and control algorithm is ran on the Raspberry Pi. 
The intrinsic and extrinsic parameters are then used to copmute real world coordinates from pixel coordinates using homography transformations as detailed below. 

## Cube and Bot Detection and Localisation
To simplify the task of bot and cube detection, the cubes are made of distinct colors (Red, Green and Blue) and the bot's top is marked with a Magenta colored arrow. Opencv's HSV filter is implemented to mask the pixels corresponding to the cubes and the bot. 
## Path-planning and  Control

## How to use the repo

