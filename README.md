This mod attempts to optimize remote vehicles for better BeamMP performance. For the player vehicle it disables collision with itself.


**Important, read before using:**
For BeamMP to work the best, the remote vehicle needs to be as similar as possible both in your game as in the game of the person driving it.
This means that the wheel and aero modifications of this mod unfortunately can cause desync. The options labeled 'Safe to use' generally don't do this, as they only edit collisions and visual effects.
Collision editing only causes desync in the event of someone crashing their vehicle, but the difference this makes for sync is negligible.


Options are in lua/ge/extensions/perfMod.lua:

**All the modifications only affect remove vehicles except reduceCollisions, which stops player vehicle colliding with itself. For remote vehicles it does heavier modifications**

--Safe to use:
1. M.reduceCollision = true -- Disables all collision for nodes not on the outer shell and self-collision for all nodes. Also disables player vehicle collision with own nodes.
2. M.disablePropsLights = true Disables headlight flares and all props except the wheel. Note: doesn't disable headlight glow and some lights that are implemented differently. Highly recommended to leave this enabled.
3. M.disableParticles = true Disables collision-based particle effects. Does not disable all particle effects

--Experimental, might cause desync but give the highest performance gain:
1. M.disableTires = true --REMOTE VEHICLES: removes tires and gives hubs tire-like properties **enabled by default but adds desync. Use at own risk**
2. M.disableAero = false --REMOTE VEHICLES: sets all aerodynamic parameters to 0 **disabled by default. Adds desync**

Current bugs: 
1. Player can't tow trailers because of reduced collisions. Could be fixed by excluding the critical nodes from the modifications.
2. **Incompatibility with the following mods**:
   1. Scintilla GT3. Fixed on rigged servers but elsewhere this car is incompatible with disableTires.
   2. Very rarely cobalt radar. That mod has some missing nil-checks that sometimes throw a fatal exception. If this happens, just reload the affected vehicle with CTRL+R

Performance comparison with unmodded game running 20 AI-driven covets on the Automation Test Track with 'High' graphics preset:
![image](https://github.com/user-attachments/assets/94d24680-cb86-4e64-a4c9-7c21b78207a4)
