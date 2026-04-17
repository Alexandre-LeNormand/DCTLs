# 3 Points Anchors PLogLin Conversion

A DaVinci Resolve DCTL that converts between log and linear using a **3-anchor model** fit to measured code values from a ColorChecker or equivalent reference chart. This DCTL is usefull when working with brackets of multiple exposures of colorcharts shot on film for film emulation purposes. Unlike PLogLin's model, this solver directly constrains all three tonal anchors — White, MidGrey, and Black — eliminating the black lift problem at low exposure settings.

## Controls
| Stops Coarse   
| Stops Fine     
| White CV       
| MidGrey CV     
| Black CV       
| Log To Linear

> **12-bit sources:** CV values on scope will be in the 0–4095 range. Divide by 4 before entering.

---

## Workflow

1. Place the DCTL node in your DaVinci Resolve color pipeline.
2. Read the 10-bit code values for the **White (CC #19)**, **MidGrey (CC #22)**, and **Black (CC #24)** patches.
3. Enter those values in the **White CV**, **MidGrey CV**, and **Black CV** sliders.
4. Use **Stops Coarse** to get to the wanted exposure in your bracket.
5. Use **Stops Fine** to trim the exposure precisely in case you need to.

---

## Why Not PLogLin?

PLogLin is a 2-parameter model constrained only at White and MidGrey. The Black CV is unconstrained, so at lower stop settings the black clips or lifts unpredictably. This 3-anchor solver explicitly forces `Black CV → lin_black`, guaranteeing no black lift across the full exposure range.

---
