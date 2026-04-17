---
title: "Model Mediated Human Teleoperation for Remote Ultrasound"
excerpt: "Development and validation of a mixed reality tele-ultrasound system" # <br/><img src='/images/500x300.png'>
collection: projects
---

Access to diagnostic ultrasound imaging remains limited in remote communities, motivating the development of tele-ultrasound to bridge this gap. Existing solutions leveraging physical robots are expensive to set up and maintain. As such, prior work introduced human teleoperation as a more accessible method of tele-ultrasound which enables tightly-coupled guidance between an expert and novice using mixed reality.

### Expert User Interface
My early contributions included developing a graphical and haptic user interface for the expert using OpenGL, OpenHaptics, and Qt. This provided a 3D-rendered visualization of the expert’s haptic device pose and enabled force feedback with the Phantom Touch X haptic device. I also integrated a communication interface using WebRTC for real-time video and data transmission between the expert and the follower’s Microsoft HoloLens 2.

![User Interface](/images/expertUI.png)


### Pilot Study and Ellipsoid Haptics
I piloted the human teleoperation system in Skidegate, Haida Gwaii, a remote island community 754 km away from Vancouver, Canada. I coordinated 11 remote abdominal ultrasound exams between UBC and Skidegate, demonstrating the feasibility of human teleoperation as a tele-ultrasound solution. To prepare for this study, I improved the reliability of the system, including implementing a method to remember the system’s state in the event of crashes. I also developed a method to estimate the patient’s torso geometry with an ellipsoid and render force feedback to the expert based on local interaction with this model. I presented this work at the 2025 IEEE Conference on Telepresence and received the Best Student Paper Award.

![Haida Gwaii overview](/images/haidaGwaiiOverview.png)

### Measurement and Potential Field-Based Patient Modelling
Model mediated teleoperation uses a model of the remote environment to provide haptic feedback to the expert, making it robust to communication delay. However, it requires a sufficiently representative model of the environment. As such, I developed a method to model the human torso geometry and stiffness using vision and force measurements and integrated this into the human teleoperation system.
I implemented a point cloud acquisition and processing pipeline in Unity for the Magic Leap 2 mixed reality headset. My method converted the raw point cloud of the patient’s torso into a structured point cloud in cylindrical coordinates using a spatial Kalman filter. This significantly reduced the network bandwidth consumption for sending the point cloud to the expert.
Using the point cloud as a boundary condition, I modelled the interior of the patient as a voxelized potential field with increasing potential deeper in the patient. With this model, I implemented a real-time 6-DOF force rendering framework based on interaction with a point shell virtual tool representation of the ultrasound probe.

To model more accurate stiffness, I developed a regularized least squares system to incorporate measured forces, torques, and probe positions in the generation of the potential field. I implemented a recursive algorithm using the CHOLMOD library to update the model in real-time. Experiments demonstrated a 71% decrease in force error and a 77% decrease in stiffness error after incorporating the measurements.

<video controls preload="metadata" width="100%">
  <source src="/videos/icra_video.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

### Publications
- **R. Yeung**, D. Black, and S.E. Salcudean. Measurement and Potential Field-Based Patient Modelling for Model-Mediated Tele-ultrasound. Accepted to 2026 IEEE International Conference on Robotics and Automation (ICRA), January 2026. DOI: [10.48550/arXiv.2509.15325](https://doi.org/10.48550/arXiv.2509.15325)
- **R. Yeung**, D. Black, P.B. Chen, V. Lessoway, J. Reid, S. Rangel-Suarez, S.D. Chang, and S.E. Salcudean. Mixed Reality Tele-Ultrasound over 750 km: A Feasibility Study. In IEEE Conference on Telepresence (Best Student Paper), September 2025. DOI: [10.48550/arXiv.2409.13058](https://arxiv.org/abs/2409.13058)