# EKF / IEKF: Kalman-gain update comparison (v3)

- Generator: built-in image_gen tool (not CLI).
- Purpose: page 8 of eskf.Rmd; preserve the user's iPad-style diagram and distinguish approximation error from measurement difference.
- Primary edit target: the user's annotated EKF/IEKF attachment in the conversation.
- Supporting style reference: ekf_iekf_relinearization_ipad_v2.png.
- Output: ekf_iekf_relinearization_ipad_v3.png.
- Earlier image versions are preserved.

## Final prompt

Use case: scientific-educational.
Asset type: a wide raster diagram for page 8 of a Korean xaringan lecture about EKF versus IEKF.
Input images: Image 1 is the user's updated annotated EKF/IEKF comparison (with μ notation and Korean captions), the primary edit target. Image 2 is the older local hand-drawn a0/a1/a2 version, a supporting pen-style reference only. Update and redraw the PRIMARY diagram, not the obsolete letter-a notation.
Primary request: retain the recognizable two-panel EKF / IEKF comparison, clean white iPad handwritten black pen style, smooth increasing convex black h(x), red / blue / green tangents, pale-blue magnifying circles, and movement from the upper right toward the lower left. Now explicitly show Kalman-gain-based state updates and a third/final update, and distinguish linearization error in the zoom from measured-minus-predicted difference. Readability over density.
Composition: wide approximately 2.4:1 landscape. Smaller EKF panel on the left, larger IEKF panel on the right. White background, no paper texture, no grids, no decorative icons. Large readable handwriting and clear mathematical subscripts. Avoid enormous headings or tiny annotation paragraphs. It will be displayed at about 1050 by 435 pixels on a slide.
Top shared note, verbatim: "같은 t · 같은 측정 z_t · 처음 prior 고정". Render z_t with a real subscript. Show a small second note "prior: μ̄_t, Σ̄_t" with bars rendered correctly.
Left EKF: heading "EKF", subtitle "한 번 선형화 + 보정". Draw x horizontal and h(x) vertical axes, black increasing convex curve. Red tangent H_t at the right-hand initial point, whose x-position is μ̄_t. Show a single clear arrow labeled "K_t로 보정" to a leftward corrected estimate μ_t. It is a state-estimate update, not a vertical measurement gap. No subsequent tangent/update in this panel. Retain a simple pale-blue zoom at a fixed arbitrary x_ref comparing black curve and red tangent; this x_ref is NOT μ_t and NOT a known true state.
Right IEKF: heading "IEKF", subtitle "보정한 추정값에서 재선형화". Black increasing convex curve and axes. Four distinct successive nominal/mean x-positions, in decreasing x from right to left:
RED μ_{t,0}=μ̄_t, BLUE μ_{t,1}, GREEN μ_{t,2}, and a BLACK OPEN CIRCLE μ_{t,3} just slightly to the left of green. Place each point on the black curve (vertical coordinate denotes the predicted measurement h at that state). Clear dashed projections to x-axis, stagger labels if necessary.
Draw only THREE straight tangents touching the curve at red, blue, green points with labels H_{t,0}, H_{t,1}, H_{t,2}. Tangents must be straight and look tangent to the curve at their own point. Red slope steepest, blue intermediate, green shallower. Do not draw a fourth tangent at μ_{t,3}.
Above the curve draw THREE leftward update arrows with readable labels: red-to-blue "K_{t,0}로 보정"; blue-to-green "K_{t,1}로 보정"; green-to-black-open-circle "K_{t,2}로 보정". The last step can be shown with a short leader and label to avoid overlap. Make every arrow actually point to the next state. The Kalman gain labels denote the full IEKF mean update with the prior correction, not gain times a pure residual added naively to the current mean.
Retain a pale-blue circular zoom comparing the black curve to red/blue/green linear approximations at one common x_ref distinct from the four iterate positions. The zoom shows black top, green nearer, blue below, red below, conceptually improved linearization at that fixed point. Label that zoom "근사 오차 ≠ 측정값 차이". This is explanatory and must NOT be connected by an update arrow as though this gap generates state updates.
Across the bottom, two SHORT explanations, no long block of equations:
"확대 원: 같은 x_ref에서 곡선과 접선의 차이"
"보정: z_t − h(μ_{t,j})와 prior 보정항에 Kalman gain 적용"
Small final note: "x_ref는 비교 위치 · 실제 정답이나 수렴 목표가 아님"
Use real Greek μ (mu) consistently, NEVER Latin u. Render all subscripts mathematically. Do not introduce ESKF δ variables, S_t, r_t, or x_true. Do not claim guaranteed convergence, monotonic accuracy improvement, or convergence to true state. This is a qualitative conceptual illustration, not numerical simulation. Preserve warm handwritten reference character, clean strokes, strong contrast, ample spacing. No clipped labels, overlaps, watermarks, logos, or decorative background.

