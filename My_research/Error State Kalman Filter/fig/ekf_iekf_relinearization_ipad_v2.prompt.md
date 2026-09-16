# EKF / IEKF downward-left comparison

Mode: built-in image_gen.
Final asset: ekf_iekf_relinearization_ipad_v2.png
Preserved previous version: ekf_iekf_relinearization_ipad.png

Style reference: taylor_2nd_order.png.
Geometry reference: a deterministic 2D sketch of h(u) = 1.5 + 0.18 u^2, evaluated at fixed x = 1.5 with tangent contact points a0 = 3.8, a1 = 2.8, a2 = 2.4. These numbers are only construction aids; they are not printed in the artwork. The approximate function values at fixed x are all below the true function value, with the gaps shrinking as the contact point moves left. Both main graphs and zooms use the same tangent equations.

## Final prompt

Use case: scientific-educational / style-transfer.
Image 1 is the EXACT SCIENTIFIC LAYOUT AND GEOMETRY to preserve. Image 2 is ONLY the user's iPad HANDWRITING AND STROKE STYLE reference.

Restyle Image 1 to look hand-drawn by the same person who drew Image 2. This is a tracing/style task, NOT a redesign. Keep Image 1's two graphs, curves, straight tangent locations, all contact dots, all fixed-x approximate-value dots, zoom contents, x/a axis positions, arrow directions, and scale relationships EXACTLY where they are. You may make strokes thicker and slightly organic, change typed text to large casual Apple Pencil handwriting, and enlarge dots, but must NOT move graph geometry.

Critical mathematical invariants from Image 1:
- Right/high red a or a0 is the initial tangent contact. Red line passes exactly through that point and extends DOWN-LEFT to the low blue/red approximation at the fixed x on the left.
- IEKF uses successively more left/lower contact points a0 -> a1 -> a2. The SAME fixed x lies to the left of all contact points.
- At that x the red tangent is lowest, blue next, green nearest the black curve. ALL colored tangents are STRAIGHT, with the slopes in Image 1, including inside the zoom circles.
- Do NOT replace the shallow convex black curve with an exponential.
- Do NOT make the approximation lines parallel, curved, disconnected, or miss their contact dots.
- The blue x markers identify the same fixed evaluation coordinate on the axis; contact points are a, a0, a1, a2.
- All iteration arrows point down-left.

Style: white background, bold black freehand axes and curve, vivid red/blue/green straight approximation lines, pale blue zoom circles/leaders, personal thick Apple Pencil handwriting exactly like Image 2. Flat 2D lecture sketch. A little pen variation is fine, but geometric relationships are fixed. No paper textures, no shadows, no 3D, no extra boxes.
Keep all text in Image 1 and no other text, converting labels a0 a1 a2 to handwritten subscript a_0 a_1 a_2. Headers: "EKF", "IEKF". Captions: "Linearize once", "Re-linearize toward x".
Output same landscape aspect ratio, entire illustration visible with margins.

