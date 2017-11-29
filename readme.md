# Multiple-Projector Spherical Screen Calibration

Source code for the paper:

Q. Zhou, G. Miller, K. Wu and S. Fels. [Automatic calibration of a multiple-projector spherical fish tank VR display](http://ieeexplore.ieee.org/abstract/document/7926707/). WACV 2017.

- Automatic Calibration Approach
  - ​
- Semi-automatic Calibration Approach
  - ​
- Video: https://youtu.be/Dgs4FmHCvp8

# Demo

- Camera intrinsic calibration example
  - File: CameraCalibApplication.cpp
  - How-to-use: Press 's' to start, then detection will be automatic (roughly 2 Sec per frame). Once it reaches a minimum amount of frames, the calibration will be triggered, then cleaning will be done to remove frames with large reprojection errors. By the end of calibration, camera intrinsic will be saved (normally with the reprojection error no more than 0.3).
  - Video: https://youtu.be/_vp6XlQdERg
  - Notes: 
    - If strong distortions on lens: make sure the chart reaches image plane boundaries so that barrel curves can be observed.
    - When spatial variance of the board is small, reprojection error would be high.
- Projector intrinsic calibration example
  - File: ProjectorCalibApplication.cpp
  - How-to-use: Right click mouse in the camera window once both the projected pattern and physical pattern are inside the camera view. Once it reaches a minimum amount of frames, the calibration will be triggered, then cleaning will be done to remove frames with large reprojection errors. By the end of calibration, projector intrinsic will be saved (normally with the reprojection error no more than 0.5).
  - Video: https://youtu.be/gG2URmbu0Ik
  - Notes:
    - Only one projector + primary monitor are connected when running. 
    - The board should be rigid and as close to a plane as possible. 

    - When spatial variance of the board is small, reprojection error would be high.
- Spherical display calibration example
  - File: SphericalDisplayCalibApplication.cpp, main_automatic_calib.m or main_semiauto_calib.m
  - How-to-use: 
    - Run SphericalDisplayCalibApplication.cpp, follow the instruction on the console window: 1. determine the projector order (projector #1, #2, etc); 2. define the projection circle (by clicking on the circle) on the spherical screen so that all pattern features are within the circle from the camera view; 3. blob projection and detection will be triggered for each projector; reprojection error will show up for each projector if it is in the Semi-automatic mode (normally below 2). 4. Once all projectors have projected, feature data will be saved. If it is in the Semi-automatic mode, the initial guess of projector extrinsics and sphere pose will also be save. 
    - Run main_automatic_calib.m if using automatic calibration mode, or main_semiauto_calib.m if using automatic calibration mode. 
  - Video:
  - Notes:
    - When the baseline between camera and projector is too short, the fundamental matrix might be inaccurate.
    - When observed projection area on Surface is too small (close to a plane), the  fundamental matrix might be inaccurate. 
    - Turn off any auto-functionalities on the projector: auto-keystone correction etc.
    - Blob detection is lighting-sensitive. May require to tweak detector params of these two. Currently the accuracy of detection depends on the light condition, improvements are on the way for different light conditions by automatically adjusting exposure/shutter speed based on captured images.
    - Be careful with out-of-focus area: if overlapping area is out-of-focus by projector, the ghosting effect is likely to happen. 

# Dependency

- OpenCV-2.4.13

- glew-1.12.0

- glfw-3.2

- glm-0.9.4.0

- FlyCapture2-2.9.3.43

# Hardware

- Camera: Flea3 [FL3-U3-13Y3M-C](https://www.ptgrey.com/flea3-13-mp-mono-usb3-vision-vita-1300-camera)
- Projector: Asus [P2B](https://www.google.ca/search?q=Asus+P2B&oq=Asus+P2B&aqs=chrome..69i57j0l5.391j0j7&sourceid=chrome&ie=UTF-8) 



