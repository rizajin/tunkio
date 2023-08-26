# RUI roadmap
All from scratch, because..., (I can?!) also the name, RUIIIIIII-KEN! (to be pronounced angrily in Japanese anime style when the attack is about to start, you can imagine yourself making shoryuken through the roof of your apartment while yelling it.. like.. I'm sorry, I got carried.. well, not sorry. YOU GET THE IDEA..)  

## Important points in this FW
1. This backend is connected to some instance that comes outside from it (Game Engine)  
2. The whole thing should mostly work on top of compute  
3. Constant performance analysis using fuzzy modules as evaluators (or something similar)  
4. Threading needs to be cooperative with the user (at this point the Game Engine or Map Editor or both, generalize, generalize..)  
5. Hybrid model of retained and immediate mode for UI, with focus more on immediate mode (because why'd be boring..)  
6. Modern graphics API's only (Direct3D12, Vulkan, Metal, WebGPU)  

## The Plan, Research and whatnots
1. 2D library(Should be 3D actually and most likely will be convertible at least), the good work horse for UI lib  
2. Rendering backends support (listed in important points)  
3. Platforms support  (Windows, Macos, Linux in Wayland and X11, iOS, Android)  

### Development of the 2D Drawing library
Window creation  (outside mini library)  
Events handling  (^ as that)

Primitives:  
- Lines, rectangles, circles, paths etc  

Transformations:
- Should come from generalized maths library(lets do that too and use the principle x<=4 components is same cost by default)  

Colors:
- Solids, fills, gradients etc..

Text:
- Basically something like freetype would be used here, but.  
- New way of doing fonts, Font engine in 3D  
- Glyph representation, vector-based, convertibles(demo from this could be nice?)  
- Font rendering techniques, lets forget the traditional stuff.. the new ones, might write a topic about this but hey..    
- Layoutting, kerning, lines, word wraps
- Font file format, (font stuff as a separate lib? most likely yes)  

Anti-aliasing:
- Super Sampling, Multi Sampling, Coverage Sampling, Fast Approx, Temporal, Morphological(MLAA, SMAA?), DLSS.. and possibly raytraced (speed analysis)  

Clipping and Layering:
- Portions drawing at least, masking(?)  

Blending:
- multiply, overlay, screen, darken, lighten, dodge, burn hard/soft, diff, excluse, hue, saturation, luminocity etc.(not sure of all but listing anyway..)  

### Development of the UI library
Widget base & system:
- Minimal inheritance, more towards composition  

Event propagation:
- widget level or pull based run(?)

Layoutting, Layout managers etc:
- Can be automatically arranged
- Can be user defined

Styles, themes:
- Mechanism to define and/or apply styling from bottom to up

User input:
- (outside) Mouse, KB, Controllers(Gamepads&related), Touch

Promptable base:
- If this topic is interesting to you, you know what this is :D (separate lib?) 

### Library development time, Testing, Debugging and Profiling
Testing:
- "GTest" but lets use the "The testing framework" (*TTF) so that the imaging systems in it can be developed for towards multiplatforms  
- Units  
- Integration  
- System  
- Imaginery  
- Performance  
- _... Yes there are loads more and kind of not wanting to list_  

Debug tools:
- Addon visualization for elements that come out from either 2D or UI  

Profiling:
- "TTF"  
- Internal speed reports  

### Documentation
Documentation:
- Code as documentation  
- Comment format as output for JDoc or similar tooling  
- Tutorials  

### The hybrid, hardways and do I need a cocktail for this to work or to work at all, lol?
Combination of retained mode and immediate mode gui:
(as some of the readers will understand or know, there is design issues when combining the two ways)
- Statefull vs Stateless  
- Event-driven vs Procedural  
- Redrawing (Implicit vs Explicit)  
- INTUITIVE, last and the most important thing for brainiacs alike.  
- Well, I kind of a have thought these things in my head but as things get complicated, the "Hattuvakio":s(fudge factors) tend to be not enough.  