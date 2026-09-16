# EKF / IEKF re-linearization illustration

Mode: built-in image_gen.
Final asset: ekf_iekf_relinearization_ipad.png
Style references: taylor_2nd_order.png (main, zoom inset); 1st_order_ekf.png (supporting).

## Generation prompt

Use case: scientific-educational.
Asset type: one hand-drawn raster illustration for slide 17 in an EKF/IEKF lecture. Generate a wide 16:9 image, pure white background, high resolution.

Input images: Image 1 (taylor_2nd_order.png) is the MAIN STYLE REFERENCE, particularly its light-blue magnifying circle showing a black nonlinear curve and a red straight tangent with a visible gap. Image 2 (1st_order_ekf.png) is a supporting STYLE reference. Create NEW content. Do not duplicate their formulas or use a second-order approximation.

Primary request: a very simple TWO-DIMENSIONAL visual comparison of EKF linearizing once versus IEKF repeatedly moving its linearization point. Match the user's thick, slightly imperfect iPad Apple Pencil handwriting and line strokes. No polished vector typography, no 3D, no shadows, no realistic paper texture, no decorative boxes.

Composition: two equal side-by-side panels on white, left titled exactly "EKF", right titled exactly "IEKF". Sparse marks, large readable handwriting, ample margins. Both panels show the SAME black smooth increasing convex nonlinear curve on small black x/y axes, with the handwritten label "h(x)" next to the curve and "x" at the horizontal axis tip. Use only black, red, vivid blue, green, and pale blue. The schematic is about local linearization mismatch, not a numerical solver or guaranteed recovery of the true state.

LEFT / EKF:
- One red straight tangent touching the black curve at an initial point toward the left. Label it "H_t".
- The tangent then visibly diverges below the curve toward the right.
- Choose a local comparison location toward the right, mark a thin pale gray vertical guide and a blue short vertical bracket between the black curve and the red tangent at that location.
- A pale-blue circle magnifies that local gap, connected by a pale-blue leader exactly in the informal style of the first reference's zoom inset. Inside it, the black curve is above the red STRAIGHT tangent and the separation is clearly visible.
- Short handwritten caption underneath: "Linearize once".

RIGHT / IEKF:
- The black curve is exactly the same shape.
- Draw THREE straight tangent segments touching it at successively further-right points. The initial tangent is red, the next is vivid blue, the final one is green. Tangent contact points move left-to-right toward the same local comparison region, and slopes increase for the convex curve.
- Label the three tangents with simple handwritten "H_0", "H_1", "H_2". Small curved arrows connect the three contact points, showing re-linearization.
- At the comparison vertical guide, the red tangent has a large gap below the curve, the blue tangent a smaller gap, and the green tangent the smallest gap. Tangents must NOT merely be parallel translated lines: each has the slope of the black curve at its own contact point.
- A matching pale-blue circular zoom inset shows the black nonlinear curve and the three STRAIGHT approximate tangent segments, with the red gap large, blue smaller, and green very small. Keep the zoom sparse and labels outside it.
- Short handwritten caption underneath: "Re-linearize: 0 -> 1 -> 2".

Text constraints: only the specified headers, captions, axis labels, tangent labels. Draw no dense equations, no covariance matrices, no invented numerical measurements, no legend clutter. Clearly all colored approximations are FIRST-ORDER STRAIGHT LINES, including the green line. Do not depict a green second-order curved fit, do not show multiple time steps or multiple measurement lines. This is one local example of improving the approximation by moving the tangent point, not a claim of monotonic convergence for every IEKF. Preserve the energetic personal iPad sketch style, large well-spaced elements, and predominantly white background.

## Final refinement prompt

Edit this two-panel EKF/IEKF illustration. KEEP the exact existing composition, black curves, axes, blue magnification circles, all handwritten captions and labels, pure white background, and the user's informal thick iPad/Apple Pencil strokes.

Only fix the scientific geometry of the colored FIRST-ORDER TANGENTS and gap markers:
1. In both magnified circles, every colored approximation must be a SINGLE STRAIGHT LINE segment. In particular the right inset's green and blue lines must NOT curve with the black curve. Keep the black curve curved. In the right inset arrange red, then blue, then green straight lines progressively nearer the black curve in the local comparison region, with progressively steeper slopes.
2. In the RIGHT main graph, make each red, blue, green straight tangent pass THROUGH its own colored contact dot on the black curve and match the local slope there. In particular the blue line currently misses its blue dot; correct that. Keep the three original left-to-right contact locations and arrows.
3. Remove ALL red, blue, and green I-shaped vertical gap brackets in the RIGHT main graph and RIGHT zoom circle. They currently look like stacked lengths; the separations between the curve and the three straight lines already show the decreasing gap clearly without these bars. Keep the LEFT blue gap bracket and both pale-blue zoom circles.
4. In the RIGHT main graph, extend the early red and middle blue tangent very lightly as straight dashed continuations toward the pale-gray vertical comparison guide, so the inset represents their extensions at that same location. Keep their solid tangent segments short. Keep the final green tangent solid.

Do not change any wording or add any text. No second-order curved approximations. No new panels, no equations, no external decorations. Preserve the original visual style and clear white margins.

