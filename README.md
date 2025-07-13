C-RAM Demonstration

An interactive, browser-based simulation of a modern Counter-Rocket, Artillery, and Mortar (C-RAM) weapon system. This project uses HTML5 Canvas and vanilla JavaScript to create a dynamic and visually engaging demonstration of an autonomous air defense battery engaging multiple incoming threats with an advanced, multi-layered AI.

Live Demo

https://amygdela09.github.io/C-RAM-Demonstration/

Key Features

This simulation goes beyond a simple game to model several key aspects of a real-world automated defense system.

    Autonomous C-RAM Battery: Control is given to a battery of three independent C-RAM turrets that must work in concert to defend a wide area.

    Realistic Ballistics & Physics:

        Projectile Drag: C-RAM projectiles lose velocity over distance, simulating air resistance.

        Ballistic Trajectories: Incoming missiles follow a parabolic arc influenced by gravity, simulating the flight path of long-range munitions.

        Overflight Trajectories: Missiles that evade the defense network are targeting locations far behind the C-RAM battery. They will fly over the turrets and off-screen, simulating a successful "leak" through the defenses.

    Cinematic Visuals & Atmosphere:

        Dynamic Particle Effects: Missiles feature fiery engine trails, and impacts create flashes and debris.

        Enhanced Explosions: Successful intercepts trigger a bright flash, a secondary fiery particle burst, and an expanding shockwave.

        Slow-Motion Kills: The simulation briefly enters slow-motion upon a successful missile intercept, highlighting the moment of destruction.

        Large-Scale Battlefield: All visual elements are scaled down to create the impression of a massive engagement area viewed from a distance.

        Atmospheric Background: A static, pre-rendered background depicts a war-torn city skyline at night, creating a sense of scale and context.

    Dynamic UI & Performance Metrics:

        A real-time UI provides critical battle information, including the number of active threats and the operational status of the defense battery.

        A live "Kill %" success rating provides instant feedback on the system's overall effectiveness.

The Battle Management AI (v4.0)

The core of this simulation is the advanced, centralized AI that controls the C-RAM battery. It is designed to be more intelligent than a simple "shoot the closest target" system, making calculated, tactical decisions every frame to maximize the battery's effectiveness, especially during high-saturation attacks.
1. Threat Prioritization

The AI's first task is to understand the battlefield.

    It constantly scans the airspace for all incoming, un-engaged missiles.

    For each threat, it uses a quadratic formula (y = y₀ + v₀t + ½at²) to calculate its Time to Impact—the precise moment it will hit the ground.

    It then sorts all hostile targets into a priority list, with the missile that will land the soonest ranked as the highest priority threat.

2. Optimal Resource Allocation (Engagement Scoring)

With a prioritized threat list, the AI must decide which weapon to use.

    It takes the single highest-priority threat from its list.

    It then assesses every available C-RAM turret to determine which one is best positioned to engage that specific missile.

    The "best" turret is determined by an Engagement Score, a weighted calculation that considers multiple tactical factors:

        Time to Aim (Weight: High): How quickly can the turret slew its barrel to the calculated intercept point? A lower time to aim results in a much higher score.

        Firing Arc Centeredness (Weight: Medium): Is the intercept point in the center of the turret's firing arc, or at an extreme edge? A more centered shot is considered more optimal and receives a higher score.

    The AI assigns the high-priority missile to the turret with the highest overall Engagement Score. This process repeats for the next most dangerous missile and the remaining available turrets.

3. Rules of Engagement

The AI and turrets operate under a strict set of rules to ensure efficiency and realism.

    Centralized Command: Individual turrets do not make their own targeting decisions. They follow the commands from the central Battle Management AI exclusively.

    Commitment: Once a turret is assigned a target, it will engage that target until it is destroyed or is no longer a factor. This prevents the AI paralysis that can occur when multiple units second-guess their assignments.

    Physical Limits: Each turret has a restricted 150-degree forward-facing firing arc. The AI will not assign a target to a turret if the required intercept angle falls outside this arc.

    Cease Fire Logic: A turret will automatically disengage and report as "available" if its target is destroyed or passes the defense line (flies below the turret's horizontal plane), preventing it from wasting time and ammunition tracking threats that have already missed.

Technical Stack

    HTML5 Canvas: Used for all rendering and visual effects.

    JavaScript (ES6+): Powers all simulation logic, physics, AI, and user interaction. No external libraries or frameworks are used.

    CSS3 / Tailwind CSS: Used for styling the UI overlay and control panel.

How to Run Locally

    Clone this repository to your local machine.

    Open the index.html file in any modern web browser.

    Click the "LAUNCH INCOMING" button to begin the simulation.

License:
    MIT License. Check the LICENSE file for details.
