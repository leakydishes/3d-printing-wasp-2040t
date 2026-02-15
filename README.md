# 3d-printing-wasp-2040t
Setup notes, Cura profile info, and start/end G-code for the Delta WASP 2040 TURBO2 with Clay Kit 3.0.

# Delta WASP 2040 TURBO2 - Clay Printing Notes (Clay Kit 3.0)

## Printer Overview

**Delta WASP 2040 TURBO2**
- **Clay Kit:** 3.0 (LDM WASP Extruder)
- **Operating systems:** Windows, Mac, Linux
- **Slicing software:** compatible with all slicing software (Cura - Slic3r - Simplify3D)
- **File types:** `.stl`, `.obj`, `.gcode`

---

## Cura Settings

### Start G-code

```gcode
G28 ;Home
M302 S0 ;Set cold extrusion
M92 E400 ;E Steps at 400 steps/mm M92 E-400 reverse
G1 Z15.0 F6000 ;Move the platform down 15mm
;Prime the extruder
G92 E0
G1 F200 E3
G92 E0
```

### End G-code

```gcode
M104 S0
M140 S0
;Retract the filament
G92 E1
G1 E-1 F300
G28 X0 Y0
M84
```

---

## Cura Profile

- **ClayCuraProfile_nossle_3mm_base**

### Cura
- **ClayCuraProfile_nossle_3mm_base**

---

## Material Setting

_TODO: add your material settings here (e.g., clay type, moisture level, retraction behavior, flow, etc.)._

---

## Clay Consistency

**Clay Consistency (left to wet, right good)**  
_TODO: add notes / photos / observations._

---

## Platform Height

**Platform height with current Z setting:** ~399.00 (**~1.5 cm**)  
_TODO: add any leveling notes, offsets, or calibration steps._

---

## Day Two Outcomes

_TODO: record outcomes (what worked, what failed, what changed, next steps)._

---

## Additional Information

_TODO: add troubleshooting notes, best practices, and any observed issues._

---

## References

- https://3d.si.edu/object/3d/beaker-vase-one-pair-f1992271:6957e595-2bfc-4f63-b074-1307158428d1
- https://wikifactory.com/@jonathankeep/cura-for-clay-3d-printing
- https://www.3dwasp.com/en/fast-3d-printer-delta-wasp-2040-turbo2/
- https://deltawasp.com.au/shop/clay-kit-3/
- https://wikifactory.com/@jonathankeep/cura-for-clay-3d-printing
- https://www.youtube.com/watch?v=Ugy0mnYmouY
- https://www.3dwasp.com/en/faq/what-to-do-if-material-comes-out-from-above-the-extruder/
- https://digitalfactory.ultimaker.com/app/library
- https://www.3dwasp.com/wp-content/uploads/2019/09/Manual-Delta-WASP-2040-Clay.pdf
- https://wikifactory.com/@vicckkky/flsun-sr-clay-conversion

---

## License
This work is licensed under **Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)**.  
You may use and adapt it for **non-commercial purposes** with **attribution**. Commercial use requires permission.
