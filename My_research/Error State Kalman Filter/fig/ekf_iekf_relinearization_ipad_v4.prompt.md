# EKF / IEKF precise tangent and true-state diagram (v4)

- Generator: built-in image_gen (not CLI).
- Edit target: ekf_iekf_relinearization_ipad_v3.png.
- Purpose: page 8 of eskf.Rmd; align points, continuous tangents, and zoomed geometry, and distinguish unknown true state x_t from final estimate mu_{t,3}.
- Output: ekf_iekf_relinearization_ipad_v4.png.
- Earlier versions preserved.

## Initial prompt (discarded output: tangent extensions were still incomplete)

Use case: scientific-educational.
Edit target: the supplied EKF / IEKF iPad handwritten diagram. Preserve its white background, hand-lettered Korean, red/blue/green thin straight tangents, smooth black convex curve, pale-blue magnifying circles, left EKF and right IEKF panels, and wide approximately 2.4:1 layout. Output a corrected, precise geometry diagram, not a loose sketch. The user specifically rejected disconnected tangents, dots off lines, and inset geometry that does not match the main diagram.

PRIMARY CORRECTIONS:
1. Every colored tangent must be ONE continuous straight line from the left-side evaluation position all the way through its own colored point on the black curve and slightly past it. No broken/gapped or parallel offset segments. It must touch the curve with matching slope at that point, not cross at an angle.
2. Every colored point is exactly centered on both its tangent and the black curve. Dashed x-axis projections share that point's exact horizontal coordinate.
3. Show an unknown TRUE STATE x_t distinctly from the estimates. Add a FILLED BLACK DOT on the black curve to the LEFT of ALL estimate positions in each main panel. Its vertical projection on the horizontal axis is labeled x_t. Next to it write "추정하려는 실제 상태" and "(x_t, h(x_t))". This is the true state drawn for teaching; the filter does not know it. Keep μ_{t,3} as a separate OPEN BLACK CIRCLE to the right of x_t in the IEKF panel. Never merge them and never label μ_{t,3} as the truth.
4. At the exact x_t vertical line on each panel, put the black truth dot on the curve and small colored dots on the tangent(s). ALL these comparison dots are on that ONE vertical dashed line. Their heights must agree with the straight lines drawn in the main panel. Make a small pale-blue source circle around that stack, and connect the source-circle perimeter to the corresponding large magnifying-circle perimeter (not to an unrelated point).
5. Each magnifying inset is a UNIFORMLY SCALED enlargement of that SAME local main-plot geometry: same slopes, relative gaps, color sequence, points-on-lines, black curve shape, and vertical alignment. Do NOT invent generic parallel lines in the inset. Red is steeper than blue, blue steeper than green. Black curve at x_t is shallower than all three. Inside IEKF zoom, at the central dashed line, heights top to bottom are black (true h(x_t)), green, blue, red. The inset contains NO iterate centers; all colored dots here are evaluations at x_t, not μ positions.

GEOMETRY GUIDE, not text to print:
Use a quadratic convex curve conceptually h(x)=2+0.3*x^2, true x_t=2.0, initial μ0=4.0, μ1=3.0, μ2=2.6, μ3=2.35. These illustrative positions are NOT claimed numerical IEKF iterates; arrows are conceptual.
Tangents: red L0(x)=2.4*x-2.8; blue L1(x)=1.8*x-0.7; green L2(x)=1.56*x-0.028.
At x_t=2: black h=3.2, red=2.0, blue=2.9, green=3.092. Thus black-green gap is small but visible, green-blue gap about twice larger, blue-red gap much larger. Show the same proportional gaps in main and zoom. Initial red point (4,6.8), blue (3,4.7), green (2.6,4.028), open final circle (2.35,3.65675). Scale and translate panels/insets as needed, preserving collinearity and tangency. The inset only shows a SHORT horizontal window around true x_t so tangents do not cross inside it. Values/functions above are construction guidance only; DO NOT print numeric coordinates or equations for this illustrative quadratic.

LEFT EKF:
"EKF", subtitle "한 번 선형화 + 보정".
One red tangent H_t through the initial red dot at μ̄_t. One leftward black arrow "K_t로 보정" to a blue estimate point μ_t on the curve at x=3.0. No blue tangent (EKF linearizes only once).
Also show separate filled true-state point at x_t=2.0 and the red tangent comparison dot below it, with a faithful magnifying inset.

RIGHT IEKF:
"IEKF", subtitle "보정한 추정값에서 재선형화".
Initial red μ_{t,0}=μ̄_t on right; blue μ_{t,1} to its left; green μ_{t,2} further left; OPEN BLACK μ_{t,3} further left; FILLED BLACK true x_t still further left.
Three correctly directed arrows located away from tangents: "K_{t,0}로 보정" red→blue, "K_{t,1}로 보정" blue→green, "K_{t,2}로 보정" green→open. Use staggered leaders so labels do not overlap. Label tangent slopes H_{t,0}, H_{t,1}, H_{t,2}. No tangent at μ3. Actual state x_t must not be an arrow endpoint.
Use short leaders and staggered horizontal-axis labels to keep x_t, μ3, μ2 clear and distinct.

SHARED TEXT:
Top: "같은 t · 같은 측정 z_t · 처음 prior 고정", plus "prior: μ̄_t, Σ̄_t".
Bottom two brief notes, legible at slide size:
"확대 원: x_t에서의 근사 오차 ≠ 측정값 차이"
"보정: z_t − h(μ_{t,j})와 prior 보정항에 Kalman gain 적용"
Final small note: "x_t는 실제로 모르는 값 · μ_{t,3}은 추정값"
Remove ALL x_ref text and the old 'not a true state' labels since this corrected version explicitly illustrates the true x_t.

Constraints: Mathematical μ not Latin u. Real subscripts, bars. No noisy measurement point at h(x_t) (z_t includes noise). No guaranteed convergence-to-truth claim. Do not force μ3=x_t. Correct source-to-inset correspondence is the top priority. Keep text sparse and use generous margins; simplify placement rather than disconnect lines. No clipped labels, duplicates, extra tangents, watermarks.

## Final refinement prompt

Geometry master: C:/Users/Public/Documents/ESTsoft/CreatorTemp/iekf_geometry_guide.png, generated from iekf_geometry_guide.R using the quadratic and exact tangent equations above. Each zoom applies one uniform 2.5x scale to the same plotted geometry. This master is a layout reference; the final raster is produced by the built-in image generation tool.

Use case: scientific-educational.
Image 1 is the authoritative GEOMETRY MASTER and edit target. It was constructed mathematically from one function, its derivatives, and a uniform 2.5x magnification. ALL black/colored curves, lines, tangencies, dot centers, dashed projections, source circles, and zoom contents in Image 1 are CORRECT. Image 2 is ONLY a handwriting/style reference, and its geometry is WRONG; do not copy its geometry.

Make Image 1 into a polished iPad handwritten teaching figure in the visual pen style of Image 2. This is a restrained lettering/stroke-weight edit, NOT a redesign. Preserve Image 1's 2.4:1 canvas, panel positions, geometrical coordinates, line slopes, exact source-to-zoom geometry, and object count. White background. Thin crisp red/blue/green lines; black function, black arrow shafts, light-blue zoom outlines. Do not bend, shorten, fragment, offset, or relocate ANY tangent. In particular the red, blue and green lines must remain continuous all the way from the small source circle through their respective tangent point.

Preserve:
- Left EKF: only one red tangent H_t, red linearization point μ̄_t, blue corrected estimate μ_t WITHOUT a blue tangent, black true-state point at x_t. One K_t update arrow.
- Right IEKF: exactly three tangents red H_{t,0}, blue H_{t,1}, green H_{t,2}, through three exact contact points with the black curve. An OPEN black final-estimate point μ_{t,3} DISTINCT from a FILLED black truth point (x_t,h(x_t)). No fourth tangent. Three gain update arrows, pointing left.
- Each main-plot small light-blue circle contains the comparison at x_t: a filled black dot on h(x_t), colored dots on the continuous tangent lines DIRECTLY BELOW on the same dashed vertical. Each large zoom must reproduce those exact lines and aligned dots, same slope and gap ratios. This exact agreement is the purpose of the edit.
- In the right zoom, at the dashed vertical: black and green close together, blue a little lower, red much further below. Do not change to evenly spaced parallel lines. The small circle and zoom must match geometrically, not just in color order.
- ALL arithmetic/math uses Greek μ, bars on prior μ and Σ, correct subscripts.

Polish lettering, keep it readable, do not add objects:
Top headings "EKF" / "IEKF".
Subtitles "한 번 선형화 + 보정" / "보정한 추정값에서 재선형화".
Shared note "같은 t · 같은 측정 · 처음 prior 고정"; underneath render z_t, μ̄_t, Σ̄_t in proper math notation.
Keep "실제 상태 (미지수)" and "(x_t, h(x_t))" pointing at the filled black dot in BOTH panels.
On arrows, use "K_t로 보정" (left), and "K_{t,0}", "K_{t,1}", "K_{t,2}" (right); it is okay to add short "보정" only if it does not collide with curves/labels.
Keep x-axis x_t and μ labels directly beneath their correct dashed projections; preserve the separate offset μ_{t,3} label with its leader.

Replace the master's two bottom plain-font lines with these clean readable Korean handwritten notes, using actual math subscripts (no literal underscore text):
"화살표: Kalman gain + prior 보정항으로 mean update"
"확대 원: x_t에서의 근사 오차 ≠ 측정값 차이"
Place these side by side in a narrow light-blue outline band if space permits.
Final small note: "x_t는 모르는 실제 상태 · μ_{t,3}은 추정값"
No extra disclaimers, equations, numbers, or state symbols.

The user has repeatedly complained that points and lines do not agree. Therefore exact geometry preservation from Image 1 is FAR more important than matching Image 2's casual stroke shape. Only handwriting and minor stroke-weight polish, leave the coordinate relationships alone. No misaligned comparison dots, no gap in tangent lines, no duplicate curves, no guessed zoom content, no watermark.
