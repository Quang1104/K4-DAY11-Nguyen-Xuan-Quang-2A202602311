# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_060000.jpg
- L2+R4: LR_noM (edge)
- L4+R2: LR_noM (mid)
- L7+R3: LR_noM (center)
- L3+R8: LR_noM (center)
- L5+R1: LR_noM (center)
- L1+R7+M6: LRM (center)
- L6+R5+M4: LRM (mid)
- R6+M8: RM_noL (mid)
- R9: R_only (center)
- R10+M5: RM_noL (mid)
- M2: M_only (mid)
- M3: M_only (mid)
- M7: M_only (mid)
- M9: M_only (center)
- M10: M_only (center)
- M11: M_only (center)
- M12: M_only (center)
## adasind_086220.jpg
- L2+R1: LR_noM (mid)
- L3+R2+M1: LRM (center)
- L1+R3+M4: LRM (center)
- L4: L_only (mid)
- L5+M7: LM_noR (mid)
- R4: R_only (center)
- R5: R_only (mid)
- M2: M_only (center)
- M3: M_only (center)
- M5: M_only (mid)
- M6: M_only (mid)
- M8: M_only (center)
## adasind_102750.jpg
- L4+R1+M1: LRM (mid)
- L1+M3: LM_noR (edge)
- L2: L_only (mid)
- L3: L_only (center)
- L5: L_only (edge)
- R2+M2: RM_noL (edge)
- R3: R_only (mid)
- R4: R_only (edge)
- R5+M8: RM_noL (center)
- M4: M_only (mid)
- M5: M_only (mid)
- M6: M_only (center)
- M7: M_only (mid)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 3 | 3 | 0 | 1 | 1 | 2 | 8 |
| mid | 2 | 2 | 1 | 2 | 2 | 2 | 8 |
| edge | 0 | 1 | 1 | 1 | 1 | 1 | 0 |
