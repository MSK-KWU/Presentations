# IESKF nominal iteration illustration

- Generator: built-in image_gen tool (not CLI)
- Asset: `ieskf_nominal_iteration_ipad.png`
- Use: `eskf.Rmd`, IESKF iteration slide
- Style inspected: `taylor_2nd_order.png`, `ekf_iekf_relinearization_ipad_v2.png`
- Scientific scope: conceptual additive-error iteration at fixed t=1; three updates j=0,1,2; final nominal index 3; no true-state convergence guarantee.

## Final prompt

```text
Use case: scientific-educational.
Generate ONE new landscape raster diagram for a Korean graduate-level Kalman filter presentation. White canvas, wide 2:1 composition. Hand-drawn iPad/Apple Pencil mathematics-note style: thick slightly irregular black axes and curve, saturated red/blue/green pen annotations, one light-blue magnifying circle. Friendly informal clear Korean handwriting, very legible mathematical hats/subscripts. No polished UI cards, no paper texture, no gradients, no logos, no watermarks. Leave generous white space. Large labels, minimal text, no long derivation.

Purpose: illustrate IESKF at FIXED time t=1: start at predicted nominal x-hat_(1,0), relinearize around the current nominal, estimate an error CORRECTION delta-x-hat_(1,j), add it to nominal, and repeat. Updating nominal is explicit, not magic. The small correction at iteration j=2 ends at x-hat_(1,3); n=2 means the FINAL LINEARIZATION was at j=2, the resulting final state is j=3. This is a conceptual example of convergence, not a claim that steps always decrease or that the true state has been found.

Layout:
Top small but readable handwritten note: "같은 t = 1, 같은 측정과 prior".
Main area is one simple 2D mathematical plot filling about 75% of width, with x-axis along lower middle, y-axis at left. Vertical axis label "h(x)", horizontal axis label "x". A black smoothly increasing convex curve h(x) goes from lower-left to upper-right. THREE colored points on the curve:
- RED x-hat_(1,0) at far right, high on curve.
- BLUE x-hat_(1,1) to its left and lower on curve.
- GREEN x-hat_(1,2) further left and lower.
Positions follow this visual right-to-left order: j0 at x=80% of graph width; j1 at 52%; j2 at 34%. For illustration the final j3 nominal is very close to the left of j2 at 32%; use a small black open circle on the curve there, no true-state target label.
At EACH of the three colored points, draw a short straight TANGENT touching the BLACK curve exactly at that point, with the correct increasing slope of the convex curve, in that point's color. Label tangents respectively "H₁,₀", "H₁,₁", "H₁,₂". Keep all labels outside the strokes. Tangents need not intersect any target line. Do NOT draw a measurement target horizontal line.
Draw colored dashed vertical projections from the three points to the x-axis. Under projections label the corresponding NOMINAL values with hats: "x̂₁,₀", "x̂₁,₁", "x̂₁,₂". Show final "x̂₁,₃" near the j2 projection using a magnifying inset to avoid overlapping labels.
Below the x-axis, use horizontal leftward arrows that indicate the actual estimated CORRECTION STEPS in state coordinates:
- LONG red arrow starts directly under x̂₁,₀ and ends under x̂₁,₁; label with a hat OVER delta-x: "δx̂₁,₀".
- MEDIUM blue arrow starts directly under x̂₁,₁ and ends under x̂₁,₂; label "δx̂₁,₁".
- Very SHORT green arrow from x̂₁,₂ to x̂₁,₃; clearly show it enlarged in the light-blue magnifying circle on the upper-left or right, away from plot annotations; label "δx̂₁,₂".
No arrow ever points toward a known true x. No slope arrow is labelled as the error correction: error-correction arrows must be horizontal state-coordinate displacements.

Magnifying inset: two nearby x-axis markers x̂₁,₂ (green filled) and x̂₁,₃ (black open), a SHORT LEFTWARD green arrow between them, labelled δx̂₁,₂. Brief green text next to inset: "보정량이 충분히 작으면 종료". Keep final index 3 unambiguous.

At bottom, large one-line handwritten equation:
"x̂₁,j+1 = x̂₁,j + δx̂₁,j"
In math notation the hat for δx is over the whole delta-x correction; all x nominal symbols have hats.
Below it or adjacent in a separate line of Korean caption:
"새 nominal에서 재선형화 → error 재추정 → nominal 보정"
Small bottom note, still legible:
"수렴한 추정값 ≠ 실제값 보장"
Do not put covariance, reset proofs, or Kalman gain formulas in this image. This diagram accompanies equations on neighboring slides; it should emphasize the evolving reference point and fresh error correction each iteration, matching a hand-sketched Taylor-linearization drawing. All Korean words correct. No cropped text.
```
