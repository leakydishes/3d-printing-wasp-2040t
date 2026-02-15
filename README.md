# 3d-printing-wasp-2040t
Setup notes, Cura profile info, and start/end G-code for the Delta WASP 2040 TURBO2 with Clay Kit 3.0.

# Delta WASP 2040 TURBO2 - Clay Printing Notes (Clay Kit 3.0)

## Overview

**Delta WASP 2040 TURBO2**
- **Clay Kit:** 3.0 (LDM WASP Extruder)
- **Operating systems:** Windows, Mac, Linux
- **Slicing software:** compatible with all slicing software (Cura - Slic3r - Simplify3D)
- **File types:** `.stl`, `.obj`, `.gcode`

#### See `Additional Information` for print settings
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
- Renamed `Clay Natural` to `Clay Natural 3mm`
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

## Additional Information Settings
- **Clay Profile Settings**
| **Nozzle size (mm)**                  |                         1.8 mm |                       3.0 mm |
| ------------------------------------- | -----------------------------: | ---------------------------: |
| **--Profile--**                       | cura_profile_1_8mm.curaprofile | cura_profile_3mm.curaprofile |
| **Layer height (mm)**                 |                0.60 (1.8×0.33) |                         1.00 |
| **Initial layer height (mm)**         |               0.40 ≈(1.8×0.23) |                         0.70 |
| **Line width / extrusion width (mm)** |                            1.8 |                          3.0 |
| **Top/Bottom Line Width (mm)**        |                            1.8 |                          3.0 |
| **--Quality--**                       |                                |                              |
| **Wall thickness**                    |                            1.8 |                          3.0 |
| **Wall Line Count**                   |                              2 |                            3 |
| **--Top/Bottom--**                    |                                |                              |
| **Top/Bottom thickness (mm)**         |                            0.0 |                          0.0 |
| **Top thickness (mm)**                |                            0.0 |                          0.0 |
| **Top layers**                        |                              0 |                            0 |
| **Bottom thickness (mm)**             |                0.72 (1.8×0.40) |                         1.20 |
| **Bottom layers**                     |                              2 |                            2 |
| **Wall flow (%)**                     |                            100 |                          100 |
| **Ratio: layer height ÷ line width**  |                 0.33 (0.6/1.8) |                         0.33 |
| **--Speed--**                         |                                |                              |
| **Print Speed (mm/s)**                |                    30 (50×0.6) |                           50 |
| **Wall Speed (mm/s)**                 |                    30 (50×0.6) |                           50 |
| **Travel Speed (mm/s)**               |                             30 |                           40 |
| **Initial Layer Speed (mm/s)**        |                    12 (20×0.6) |                           20 |

- **Print Profile Settings (*Required manual input*)**
|  **--Nozzle Settings--**              |                         1.8 mm |                       3.0 mm |
| ------------------------------------- | -----------------------------: | ---------------------------: |
| **Nozzle size-**                      |                            1.8 |                          3.0 |
| **Compatible Material Diameter(mm)**  |                           2.85 |                          2.85|


|  **Materials Settings**             |                              1.8 mm |                        3.0 mm     |
| **--Profile--**                     | clay_natural_1_8mm.xml.fdm_material | clay_natural_3mm.xml.fdm_material |
| ----------------------------------- | ----------------------------------: | --------------------------------: |
| **--Information--**                 |                                     |                                   |
| **Density**                         |                                1.24 |                              1.24 |
| **Diameter**                        |                                 1.8 |                                 3 |
| **--Print Settings--**              |                                     |                                   |
| **Retraction Distance**             |             6.5 × (1.8/3.0) ≈ 3.9mm |                             6.5mm |
| **Retraction Speed**                |                              25mm/s |                            25mm/s |

- **Testing 1.8mm Nozzel**
    - Materials Settings (Print Settings) Retraction distance 6.5 × (1.8/3.0) ≈ 3.9mm next as Retraction Distance from 6.5mm

#### Notes:
##### **Quality**
- **Line width / extrusion width (mm)**: will be set by the nozzle width set in the Printer profile (i.e 3mm nozzle = 3mm line width)
- **Layer height (mm)**: 2 mm nozzle use between a 0.6 - 0.8 layer or slice height (i.e 2mm nozzle = 0.6-0.8mm layer height), (i.e 3mm nozzle = 1mm layer height)
- **Initial layer height (mm)**: half normal layer height helps the first layer stick down (i.e 3mm nozzle = 1.5-1.7mm initial layer height)

##### **Shell**
- **Wall Thickness**: same as Line Width and Nozzle (double or triple wall thickness you can increase x2 or x3 of the line width measurement (i.e 3mm nozzel/ 3mm line width = (x2) 6mm Wall thickness)
- **Wall Line Count**: default is set as 1 if the Wall Thickness is set the same as the Line Width. Optional update Wall count to 2 or 3 and the Wall Thickness becomes greyed out.
- **Top/Bottom Thickness**: gets taken from the Layer/Slice Height (keep as 0 if no base or using slab of clay to print on), 
- **Top Thickness**: without infill there is no Top in clay (set to 0)
- **Bottom Thickness**: Creates a base (if not printing onto a slab ect). If printing base, print at least 3 layers so base would be Layer Height (i.e 3mm nozzel 1.8mm = too thick, 1.2mm correct)

##### **Infill**
- **Infill Density**: open forms set to 0
- **Infill Line Distance**: not active is infill is 0.
- **[Reference](https://support.ultimaker.com/s/article/1667411002588)**

##### **Material**
- **Wall Flow**: 100% (controls flow speed, linked to the nozzle size and the material diameter).
- **Initial Layer Flow**: 100 %
- **Enable Retraction**: Activate

##### **Speed**
- Moving from 3mm to 1.8mm we scale=1.8/3.0=0.6
- **Print Speed**: 50% (3mm)
- **Wall Speed**: 50% (same as print speed)
- **Travel Speed**: the speed the machine moves from home or the top of the tower down to begin printing and the speed it moves between printing. Too fast and you can distort prints (must reduce for 1.8mm nozzle) as the printhead moves between printing areas. Set between 30 - 50 mm/s.
- **Initial Layer Speed**: 20m/s (print slower to set base) (3mm)

##### **Travel**
- **Combing Mode**: All
- **Z Hop When Retracted**: Activate
- **Z Hop Height**: Extrusion pulls up breaking the clay extrusion between printhead non printing moves (1-2 mm)

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
- https://commons.wikimedia.org/wiki/Category:STL_mathematics
- https://blogmymaze.wordpress.com/2012/06/07/different-types-of-meanders-in-greek-art/

---

## License
This work is licensed under **Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)**.  
You may use and adapt it for **non-commercial purposes** with **attribution**. Commercial use requires permission.
