2026-01-04 19:14

#Extended-Reality 
# Selection
Acquire a (or many) target usually via hand:
1. User designates an/many object(s). Must have efficient detection algorithm.
2. User confirms via button, gestures, vocal commands,...
3. System confirms, feedbacks (during selection).
## Simple Virtual Hand
By touching (+ haptic) or intersection with virtual object (no haptic).
## Ray cast
Laser pointer metaphor. Only need 2 DOF.
## Sticky finger/occlusion
Pointing a finger so that a ray from the eye through the finger intersects and selects the nearest object.
## Go-Go
Uses a nonlinear mapping where, after a threshold distance, the virtual hand moves toward the object faster than the real hand.
# Manipulation
Specify/Modify properties of *selected* object(s) (transform, color, texture,...).
Direct (virtual tools) or indirect (real tools). Disable selection during manipulation.
## Simple Virtual Hand
Just parent the object to the hand.
## HOMER
Uses ray-casting to select an object, virtual hand automatically move to it (attaching the object). Upon release, virtual hand returns to its original position.
## Scale-World Grab
When an object is selected but out of reach, the system either enlarges the user or shrinks the object so the virtual hand can touch it; if the user stays still and there’s no stereo view, the scale change is visually imperceptible.
## World-in-Miniature
A handheld miniature of the virtual world lets users manipulate or navigate full-size objects indirectly by moving their tiny counterparts.