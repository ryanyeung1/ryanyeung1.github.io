---
title: "Microfluidic Printhead Test Bench"
excerpt: "*Mar 2022 - Sep 2022*<br/>Designing a test bench for microfluidic bioprinter printheads" # <br/><img src='/images/500x300.png'>
collection: projects
---
*Mar 2022 - Sep 2022*

All manufactured bioprinter printheads must go through a series of tests for quality control. The existing setup suffered from sensor drift and required an inefficient workflow, bottlenecking manufacturing speed. I designed a new test bench to address these challenges.

The project started with a careful assessment of the functional requirements and sourcing components that met the determined specifications. The design consisted of a large microfluidics circuit with several solenoid valves for directing flow. The system was driven by a three-way syringe pump, allowing precise control over the flow rate and the ability to draw from two different sources of liquid. This was important for cleaning the bench with ethanol to prevent biofouling and sensor drift. Using a pressure sensor, I implemented a closed-loop controller to maintain specific pressures for leak testing. I developed software to interface with a programmable logic controller to actuate the valves, control the syringe pump, and obtain measurements from the pressure sensor. This enabled completely autonomous execution of the test procedures and data collection.

![User Interface](/images/aspectQCBenchPOC.jpg)

<video controls preload="metadata" width="100%">
  <source src="/videos/aspect_qc_bench.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>