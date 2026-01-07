2026-01-04 12:56

#Extended-Reality  #HCI 

> Used in digital sound, music, accessibility, telematics, 3D sound stimulation, acoustic applications, multimedia research, and [[Virtual Reality]].

# Psychoacoustics
Interaural Time Difference: sound reaches the closer ear first; 
Interaural Intensity Difference: sound louder in the closer ear.
# HRTF
Sound from a certain angle is filtered by the environment and the listener’s body (torso, head + head tracking, ears), then further processed by using the ear canal and inner ear impedance to create differences in phase and amplitude give cues for direction and distance - the perception of 3D sound => Complex with many sources but realistic.

FIR filters can be used to simulate environment (walls,...).

Tested using test dummies or by NASA: Outer ear responses are recorded with microphones, processed with FIR filters, and key features are extracted to capture and analyze how the outer ear modifies incoming sounds.
![[HRTF Test.png]]
# 3D sound cards
Four 40 MHz Motorola 56002 processors with 12 Mbit DRAM and 1.5 Mbit SRAM can handle FIR filters of up to 256,000 taps.