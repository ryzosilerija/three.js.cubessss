Assets & Blender Work
•	Frog Character
o	Modeled in Blender, exported as .glb.
o	Baked frog textures for real-time performance.
o	Frog animations exported and looped using AnimationMixer.
o	In-game: frogs spawn periodically and chase the moving block (cube1) by calculating direction vectors in JavaScript. The block was placed inside the player to give an illusion that they player is being chased by a frog, the block was connected to the camera 
•	Gun Model + Recoil Animation
o	Modeled and rigged in Blender.
o	Exported with recoil animation.
o	Integrated two versions in code:
	gunScene → static mesh (always visible).
	gunAnimated → animated version controlled by AnimationMixer.
o	Toggle between static and animated gun using the Y key.
•	Baked Textures & Environment
o	HDR sky environment (sky.exr) imported with EXRLoader.
o	Applied as both scene background and reflection map.
o	Balanced brightness using ACESFilmicToneMapping and toneMappingExposure.
________________________________________
💻 Three.js Code & Game Mechanics
•	Scene Setup (init() in code)
o	Camera wrapped inside yaw/pitch objects for FPS-style mouse look.
o	Player spawns high in the world (yawObject.position.set(0, 500, 0)).
o	Lights: hemisphere light (ambient fill) + directional sun light.
o	Renderer with antialiasing + tone mapping.
•	Movement & Physics
o	WASD controls implemented with a velocity vector.
o	Gravity constantly applied (const gravity = -0.05).
o	Ground collision detection with downward raycasting.
o	Jumping unlocked when player is grounded (canJump = true).
o	Forward collision raycasting prevents walking through walls/objects.
•	Shooting System
o	Left mouse button:
	Plays recoil animation (gunAnimatedMixer).
	Raycasts from screen center to detect hits.
	Spawns bullet hole decals (planes with transparent texture).
	If a frog is hit → set its visibility to false (frog disappears).
o	Right mouse button:
	Debug raycast → spawns red cubes at impact points.

o	Crosshair drawn with CSS (#crosshair).
o	Labels (#label, #label1, #label2) updated in animate() loop.
o	Menu system sketched out with styled buttons (.menu button).
________________________________________
🎮 Controls
•	WASD → Move
•	Mouse → Look around
•	Left Click → Shoot (recoil animation + bullet holes + frog removal)
•	Right Click → Debug cube shot
•	Y → Toggle static ↔ animated gun
•	Click on Seat → Teleport to seat + open purchase menu
________________________________________
📖 What I Did / Learned
From looking at the code and building assets, this project required combining both 3D art skills and game programming skills:
•	Modeled, textured, and animated assets in Blender, exporting them to .glb.
•	Integrated multiple GLTF models into Three.js, attaching some to the camera (gun) and leaving others in-world (frogs, seats).
•	Used AnimationMixer to drive Blender-exported animations inside the render loop.
•	Implemented first-person movement with physics, gravity, and collision detection.
•	Learned raycasting for interaction (shooting, seat selection, video plane hit detection).
•	Balanced scene lighting with tone mapping to prevent overexposure from HDR skies.
•	Implemented AI-like behavior (frogs continuously moving toward a target block).
•	Added HUD/UI elements (crosshair, interactive labels, purchase menu).

