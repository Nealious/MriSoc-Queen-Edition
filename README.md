# MriSoc-Queen-Edition
A modified version of the [mrisoc](https://github.com/mriscoc/Ender3V2S1.git) Ender-3-v2/S1 binary for the Ender-3-v2-neo.
- Supports BlTouch/CrTouch on ender 3 v2 neo.
- Supports Marlin Unified Bed Leveling.
- Supports Model Predictive Temperature Control
- Supports Auto PID tuning.
- Currently binary was built for Creality 4.2.2 only, and DACAI model display boards.
- Added the folowing g-code commands previously unavailable:
  - C10 : Mark the g-code file as a Configuration file to avoid confirm to print and print done dialogs (at least one space is currently required after the C10).
  - C11 En Rn Gn Bn : colorize UI elements (C11 E0 to update the screen)
  - C29 Ln Rn Fn Bn Tn Nn Xn Ym : set probing mesh inset (Left, Right, Front, Back) in mm.  T is the probing temperature (T0 doesn't change the current bed temperature) and N is the density or amount of grid points NxN, it is posible to set a NxM density by using X and Y. In UBL use G29 S# to save to a mesh slot number #.
  - C35 Launch the bed tramming wizard.
  - C100 Xn Yn Zn : setup minimum physical limits
  - C101 Xn Yn Zn : setup maximum physical limits
  - C102 Xn Yn : setup bed size (can't be larger than physical limits)
  - C104 U1 Tn : unlock the maximum hotend temperature temperature to ###°C (limited by thermistor calibration table CAUTION, the stock hot-end doesn't support more than 260°C due to the isolators and PTFE degradation.)
  - C108 : cancel screens waiting for user simple confirmation
  - C125 Xn Yn Zn : setup the park position
  - C250 Pn : enable or disable preview screen (needs PREVIEW_MENU_ITEM)
  - C412 Mn : set run-out sensor active state (M0:LOW, M1:HIGH, M2:MOTION)
  - C510 Un : lock/unlock the screen (C510 U1 to unlock)
  - C562 En : invert the Extruder (E1 to invert)
  - C810 An Bn Cn Dn En : sets up the toolbar shortcuts A..E to functions 0..n (0 disable that shortcut)
  - C851 Sn [Zn] Mn : Set probe Z feed speed (S) in mm/min, Multiple probing (Mn>1) or disables it (M0), in manual mesh version, Z parameter can be used to set a manual Z-offset.
- **Note:** This binary was compiled for the Neo model only, it will not work as intended on other Ender-3-V2 models, Installation is done through the same process of updating (format sdcard to fat 32, copy the binary file on the card, insert into printer, and turn on). The printer will "update" as normal. The display however needs to be dismantled and its respective binary copied on the sd card (make sure only one binary is on the card) and inserted into a hidden sd card slot on the board itself.
- **Warning:** The temperature limits and Speed controls have been removed and replaced by user specified limits under the advanced menu. If the printer is asked to go to a certain temparature within the user set range it will, regardless of possibility of damage so be careful. 
