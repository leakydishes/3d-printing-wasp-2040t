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

## Cura Machine Settings
- **WASP 2040: x width 200 mm, y depth 200, z height 400**
- **Printhead Extruder 1 set up as per image**
<p align="center">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/cura_machine_settings_1.png" alt="Machine Settings 1" width="48%">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/cura_machine_settings_2.png" alt="Machine Settings 2" width="48%">
</p>

#### Notes Machine Settings
- The nozzle size regulates the flow of material as controlled by the feed speed (different nozzle sizes require different Printer profiles)
- **Custom material** is required diameter of 1 mm, larger numbers will impact the flow rate. If 100% flow is too fast, increase the custom material diameter.

---

### Start G-code

```gcode
; --- Startup / setup ---
G28                 ; Home all axes (X/Y/Z)

M302 S0             ; Allow cold extrusion (paste/clay extruders)
M92 E400            ; Extruder steps/mm (use E-400 to reverse direction)

G1 Z15.0 F6000      ; Move to Z=15mm for clearance

; --- Prime ---
G92 E0              ; Zero extruder position
G1 F200 E3          ; Extrude 3mm to prime
G92 E0              ; Zero again for clean start
```

### End G-code

```gcode
; --- End / shutdown ---
M104 S0             ; Hotend off (safe even if not used)
M140 S0             ; Bed off (safe even if not used)

; Retract / relieve pressure
G92 E1              ; Set extruder position reference
G1 E-1 F300         ; Retract 1mm

; Park / tidy up
G28 X0 Y0           ; Home X/Y to park head

M84                 ; Disable steppers
```


---

## Extruder / Printing / Plate Height
- **Platform height with current Z setting:** ~399.00 (**~1.5 cm**)

<table>
  <tr>
    <td align="center" width="33%">
      <b>Extruder Placement</b><br>
      <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/blob/main/img/wasp_extruder_head_placement.png" alt="Extruder Placement" width="100%">
    </td>
    <td align="center" width="33%">
      <b>Printing Example</b><br>
      <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/wasp_extruder_print.png" alt="Printing Example" width="100%">
    </td>
    <td align="center" width="33%">
      <b>WASP Plate Height per Z value 399</b><br>
      <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/wasp_plate_height_per_z_value_399.png" alt="WASP Plate Height per Z value 399" width="100%">
    </td>
  </tr>
</table>

---

## Cura Profile Example
#### See directory `cura_profiles` for others
- **ClayCuraProfile_nossle_3mm_base**

<p>
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/clay_cura_profile_nozzle_3mm_base.png" alt="Clay Cura Profile - Nozzle 3mm Base" width="900">
</p>

---

## Cura Graph Cartesian coordinate

<p align="center">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/clay_cura_profile_nozzle_3mm_base_z_107.png" alt="3mm_base_z_107" width="48%">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/clay_cura_profile_nozzle_3mm_base_z_83.png" alt="3mm_base_z_83" width="48%">
</p>


---

## Material Settings (Print + Information)

<p align="center">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/cura_material_settings_print.png" alt="Material Cura Settings (Print)" width="48%">
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/cura_material_settings_information.png" alt="Material Cura Settings (Information)" width="48%">
</p>

#### Notes Machine Settings
- Create/ import `Natural Clay` profile
- Set `Retraction Distance` and all `temperatures` to 0, no internal heating required.
---


## Clay Consistency

<p>
  <b>Clay Consistency</b><br>
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/raw/main/img/clay_consistency_2.png" alt="Clay Consistency (1 too soft, 2 correct viscosity)" width="380">
</p>

- **1 — Too soft**
- **2 — Correct viscosity**

---

## Clay Outcomes

<p>
  <img src="https://github.com/leakydishes/3d-printing-wasp-2040t/blob/main/img/vase_basic_3mm_outcomes.png" alt="Clay Outcomes" width="420">
</p>

---

## Additional Information


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
