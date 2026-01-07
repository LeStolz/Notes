2026-01-05 07:26

#Extended-Reality  #HCI 

# [[3D Transform Tracking Technologies]]
# [[Visualization Technologies]]
![[Sight-based Design.png]]
![[Mono and Stereo Models.png]]
# [[Sound Technologies]]
Sounds or musical patterns accompanying events and convey information. Their meaning can be **causal** (directly linked to the action, e.g., a friction sound for object movement), **metaphorical** (e.g., a door closing to indicate an application closing), **arbitrary** (understood only through learning or experience, e.g., a simple “beep” indicating successful target acquisition), **earcons** (abstract musical patterns and must be learned, being recognized through their rhythm, pitch, and volume), **voice messages** (conveying complex information), or **music and ambient sounds** (provide contextual or atmospheric cues).
# [[Haptic Technologies]]
**Direct haptic interaction** conveys physical forces from object interactions (collisions, friction, properties like weight or texture) based on the effector’s position, using collision detection and force/torque computation.
# Guides
**Virtual guides (virtual fixtures)** provide visual, audio, or haptic assistance to help users achieve goals or respect constraints, using cues like optimal paths, restricted zones, and control–display mappings such as attraction/repulsion or constrained movements.

Degrees of assistance: 
- Sensory assistance: displaying, signaling objects, information, states or constraints.
- Inform: informing a state.
- Guidance: modifying interactions and showing relationships between states
- Motor assistance/constraint: partially or fully prevent interactions to enforce constraints.
## Audio
Convey information by directly representing data as audio or by mapping data attributes to sound properties (volume, duration, pitch, timbre, or spatial location). They may use sound processing (e.g., distortion, attenuation), sound or speech synthesis, and auralization to enhance or communicate information effectively.
## Haptic
Convey information through forces or torques, mapping data attributes to force/torque properties (intensity, direction, function) or vibrations (intensity, location, frequency, pattern) (haptization).
## Multimodal
**Sensorimotor substitution** replaces the natural sensory-motor channel used for a perception or action with another channel. For example, a backup radar converts visual information to audio, or a collision signal changes haptic feedback to sound. Using multiple channels can convey more information simultaneously and reduce cognitive load.
# Visuo-Haptic
**Haptic illusions** create sensations like bumps or holes using braking and propulsion forces, or simulate curvature by combining force cues with geometric cues.
# Guidelines
**Physical:** base on real tools, reduce weight/cables, ensure safety, comfort, short sessions, multimodal feedback, use constraints/accessories.

**High-level:** user-centered design, follow design principles, integrate tasks smoothly, prevent accidental interactions.

**General:** Use familiar techniques, adapt to devices, combine natural & magic interactions, exploit proprioception, prefer two-handed input, offer redundancy.

**Selection:** Virtual hand for naturalness, pointing for precision, adjust control–display ratio, snap or enlarge objects if needed.

**Manipulation:** Use constraints, indirect for precision, direct mapping for training transfer, reduce clutching with non-isomorphic movements.

**Navigation:** Mix physical & magic locomotion, smooth transitions, provide orientation cues, avoid instant teleportation when spatial awareness matters.

**Control:** Keep task flow, prevent mode errors, provide guidance, use 2D/1D selections, enable multimodal and intuitive commands.

**Overall:** Blend realism & non-realism, reuse known interaction techniques, respect user needs & ergonomics, 6-DOF control for best performance.