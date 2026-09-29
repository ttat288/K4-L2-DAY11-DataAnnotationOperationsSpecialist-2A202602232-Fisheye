# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_258420.jpg
- L7+R1: LR_noM (edge)
- L8+R6+M2: LRM (edge)
- L9+R4: LR_noM (center)
- L1+R3+M3: LRM (mid)
- L3+R2+M9: LRM (mid)
- L10+R5+M6: LRM (mid)
- L2: L_only (mid)
- L4: L_only (mid)
- L5: L_only (center)
- L6: L_only (mid)
- R7+M12: RM_noL (mid)
- R8: R_only (center)
- M4: M_only (edge)
- M5: M_only (mid)
- M7: M_only (mid)
- M8: M_only (center)
- M10: M_only (mid)
- M11: M_only (center)
## adasind_270517.jpg
- L2+R6+M1: LRM (mid)
- L4+R5+M3: LRM (center)
- L5+R1+M4: LRM (center)
- L3+R4: LR_noM (center)
- L6+R2: LR_noM (center)
- L1+R3+M2: LRM (edge)
- L8+R7+M8: LRM (mid)
- L7: L_only (mid)
- M5: M_only (mid)
- M6: M_only (center)
- M7: M_only (center)
- M9: M_only (center)
- M10: M_only (mid)
- M11: M_only (mid)
## adasind_310008.jpg
- L4+R3+M1: LRM (edge)
- L5+R1: LR_noM (mid)
- L2+R5+M2: LRM (edge)
- L1+R4+M4: LRM (edge)
- L3+R2+M3: LRM (edge)
- M6: M_only (mid)
- M7: M_only (mid)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 2 | 3 | 0 | 1 | 0 | 1 | 5 |
| mid | 5 | 1 | 0 | 4 | 1 | 0 | 8 |
| edge | 6 | 1 | 0 | 0 | 0 | 0 | 1 |
