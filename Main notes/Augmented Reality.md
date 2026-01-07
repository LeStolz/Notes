2025-10-14 15:36

#Extended-Reality

> Combine the real world and the virtual one
> To improve, complete, restore, predict reality by a computer
> By providing natural sensory assistance/extension to the user
> Thus, must be in real-time

# Fundamental rules of AR
Real-time (1) Interaction between the real world and the virtual one (2). Ensure content is accurately aligned (sensory coherence between the 2 worlds) (3) by using:
- Estimation of the camera's pose (transform) via view-point prediction.
- Vision based methods: sensible to mobility, luminosity, occlusion,...
- Can use VR-type devices or tangible interfaces to interact with virtual objects.
# Augmentations
Ubiquitous/Pervasive Computing refers to tiny, networked processors and sensors embedded in everyday objects, enabling seamless access to information anytime and anywhere.

Wearable computers are integrated into clothing accessories like headbands or bracelets.

![[Visual Augmentations.png]]
## To enhance user's view
### Tracking
6-DOF [[3D Transform Tracking Technologies|optical tracking]] is used with stereo vision and laser to scan depth: Time of flight => structured lights.
### HMD
Video see-through: FOV (camera) + Overlap (calculated by tracking transform and showing using a mirror).

Optical see-through: FOV + Overlap (calculated by tracking transform and showing using a mirror, occlusion of real object done by spatial light modulator).

Both: Focal distance and optical axes aligned with eyes for parallax.
### Contact lens
Micro-LED displays as lenses, very low resolution, main challenges are component miniaturization and low-efficiency (~10%) microwave signal transmission.
### Hand-held
Tracker + camera, no parallax.
## To enhance user's environment using spatial AR
Projection display (can be on HMD): FOV + overlap projected onto the object itself.
![[Illuminating Clay.png]]
We can use [[SLAM]].
## To enhance audio
Audio AR enhances the real sound environment with spatialized artificial sounds using microphones, tracking, and orientation estimated via [[Sound Technologies|ITD and IID]].
## To enhance haptics
Uses [[Haptic Technologies]] to mix real and virtual forces and visual tracking (e.g., ARToolkit) for tasks like assembling virtual parts on real objects.

Uses tactile to enhance real objects with virtual textures using [[Haptic Technologies|electro-vibration]], aligning the tactile model to the real object and tracking contact points to modulate the electric field.
## Tangible interfaces
Use physical objects as interaction media by using trackers/markers (e.g. sixth sense).

An image is rear-projected onto a table illuminated with infrared lamps; physical objects reflect the IR light, and a camera under the table detects their position and orientation. Different objects represent different interfaces.

Simple interaction using the user’s hands, no special input devices needed. Limited to 2D surfaces; 3D manipulation is very difficult.
![[Tangible Interface.png]]
## Transitional AR-VR interfaces
AR interface that can transition to VR for immersive and collaborative experiences but markers must remain visible for tracking.
# [[Application and Research of Immersive Technologies]]
# AR framework
High level: Interaction, Presentation, Authoring.
Low level: 
- Sense environment: markers, UI, gesture => API.
- Track, Calibrate transform => Rendering, Displaying technology + Registration.
# Problems
[[Recognition and 3D Registering]] in real-time and limits of visualization devices and control devices (controllers). Multiple (not fully natural) interaction styles exist due to technology limitations.