C-RAM Demonstration

An interactive, browser-based simulation of a modern Counter-Rocket, Artillery, and Mortar (C-RAM) weapon system. This project uses HTML5 Canvas and vanilla JavaScript to create a dynamic and visually engaging demonstration of an autonomous air defense battery engaging multiple incoming threats.

Try the Live Demo Here! (<- Replace with your live demo link)

Key Features
This simulation goes beyond a simple game to model several key aspects of a real-world automated defense system.

Autonomous C-RAM Battery: Control is given to a battery of three independent C-RAM turrets that must work in concert to defend a wide area.

Realistic Ballistics:

Projectile Drag: C-RAM projectiles lose velocity over distance, simulating air resistance.

Ballistic Trajectories: Incoming missiles follow a parabolic arc influenced by gravity, mimicking the path of artillery or mortar rounds.

Cinematic Visuals:

Dynamic Particle Effects: Missiles feature fiery engine trails, and impacts create flashes and debris.

Enhanced Explosions: Successful intercepts and ground impacts trigger a bright flash, a secondary fiery particle burst, and an expanding shockwave.

Slow-Motion Kills: The simulation briefly enters slow-motion upon a successful missile intercept, highlighting the moment of destruction.

Atmospheric Background: A static, pre-rendered background depicts a war-torn city skyline at night, creating a sense of scale and atmosphere.

Dynamic UI & Feedback:

A real-time UI provides critical battle information, including the number of active threats, the status of the defense battery, and a live "Kill %" success rating.

Interactive Control: The user acts as the command center, initiating missile salvos to test the limits of the C-RAM defense system.

The Battle Management AI
The core of this simulation is the AI that controls the C-RAM battery. It's designed to be more intelligent than a simple "shoot the closest target" system. The AI operates as a centralized command and control unit, making tactical decisions every frame to maximize the battery's effectiveness, especially during high-saturation attacks.

1. Threat Prioritization

The AI constantly scans the airspace for all incoming, un-engaged missiles.

For each threat, it uses a quadratic formula (y = y₀ + v₀t + ½at²) to calculate its Time to Impact—the precise moment it will hit the ground.

It then sorts all hostile targets into a priority list, with the missile that will land the soonest ranked as the highest priority.

2. Optimal Resource Allocation

The AI takes the highest-priority threat from its list.

It then assesses all available (idle) C-RAM turrets to determine which one is best positioned to engage that specific threat.

The "best" turret is not necessarily the closest one. The AI calculates an Engagement Cost for each turret, factoring in the time it will take to rotate its barrel to the required intercept angle.

The turret with the lowest engagement cost (i.e., the one that can get its weapon on target the fastest) is assigned the missile.

3. Rules of Engagement

Commitment: Once a turret is assigned a target by the central AI, it will engage that target exclusively until it is destroyed or is no longer a factor. This prevents the AI paralysis that can occur when multiple units second-guess their assignments.

Physical Limits: Each turret has a restricted 150-degree forward-facing firing arc. The AI will not assign a target to a turret if it falls outside this arc.

Cease Fire Logic: A turret will automatically disengage and report as "available" if its target is destroyed or passes the defense line (flies below the turret's horizontal plane), preventing it from wasting time and ammunition tracking threats that have already missed.

Technical Stack
HTML5 Canvas: Used for all rendering and visual effects.

JavaScript (ES6+): Powers all simulation logic, physics, AI, and user interaction. No external libraries or frameworks are used.

CSS3: Used for styling the UI overlay and control panel.

How to Run Locally
Clone this repository to your local machine.

Open the index.html file in any modern web browser.

Click the "LAUNCH INCOMING" button to begin the simulation.
