# Critic

## I. Gaussian-LIC

### 1. Fixed-radius Sky Gaussian의 확장성

Gaussian-LIC은 unbounded outdoor scene의 sky를 표현하기 위해 world origin을 중심으로 하는 큰 반지름의 upper hemisphere에 \(N_s\)개의 sky Gaussian을 무작위로 배치한다. 실험에서는 \(R=10^4\)를 고정하여 sky Gaussian이 foreground보다 충분히 뒤에 있도록 설정한다.

그러나 이 방식은 전체 camera trajectory와 scene extent가 \(R\)보다 충분히 작다는 가정에 의존한다. 장시간·대규모 incremental mapping으로 camera가 고정된 hemisphere의 경계에 가까워지면 다음 문제가 발생할 수 있다.

- Sky Gaussian에서 부자연스러운 translation parallax가 발생할 수 있음
- Sky Gaussian과 foreground Gaussian의 depth ordering이 불안정해질 수 있음
- 고정된 Gaussian 분포가 확장된 trajectory의 관측 방향을 충분히 덮지 못할 수 있음
- 다양한 scene scale에 대해 \(R\)과 \(N_s\)를 수동으로 조정해야 함

논문에서는 trajectory 또는 map extent에 따라 sky hemisphere의 중심·반지름·밀도를 갱신하는 방법을 제시하지 않는다. 따라서 Gaussian-LIC의 sky modeling은 엄밀한 의미의 unbounded representation이라기보다, 매우 큰 고정 bound를 사용하는 근사에 가깝다.
### 2. Visual SfM point > Densification 전략
- 생각해보면, SfM도 결국 Sparse 한 point
- Pose는 Coco-LIC의 Pose를 그대로 믿고 함. 따로 refinement를 거친 pose를 사용하는게 아님.


<!--
#### Potential Research Idea: Trajectory-Adaptive Infinite-Sky Gaussian

Sky를 유한한 world position의 Gaussian으로 표현하지 않고, camera translation에 영향을 받지 않는 directional representation으로 분리할 수 있다.

- Sky Gaussian의 위치 대신 unit sphere 위의 방향 \((\theta,\phi)\)을 최적화
- Camera rotation에 의해서만 sky projection이 변하도록 설계
- Camera translation과 무관한 infinite-depth background layer로 rendering
- 관측 방향과 reconstruction uncertainty에 따라 directional Gaussian을 adaptive densification/pruning
- Foreground 3D Gaussian map과 sky representation을 분리하여 각각 독립적으로 최적화

이 접근은 고정된 \(R\)에 대한 의존성을 제거하고, 장거리 incremental mapping에서도 sky의 parallax와 depth-ordering artifact를 줄일 가능성이 있다. 실험에서는 trajectory 길이와 map extent를 증가시키면서 sky-region PSNR/SSIM/LPIPS, Gaussian 개수, memory, rendering speed를 Gaussian-LIC의 fixed-hemisphere 방식과 비교할 수 있다.
-->

## II. Gaussian-LIC2

### 1. Depth Completion 기반 Blind-area Gaussian 초기화의 신뢰성

Gaussian-LIC2는 현재 RGB image와 최근 frame들의 sparse LiDAR depth를 SPNet에 입력하여 dense depth를 생성한다. 이후 LiDAR depth가 존재하지 않는 image patch에서 completion depth가 가장 작은 pixel 하나를 선택하고, 해당 pixel의 RGB와 예측 depth를 이용해 3D colorized point를 생성한 뒤 새로운 Gaussian을 초기화한다.

그러나 이 과정에는 다음과 같은 명확한 한계가 있다.

1. **실제로 보완하려는 blind area에서는 completion 결과를 직접 검증할 수 없다.**  
   Depth completion의 신뢰도 검사는 LiDAR depth가 존재하는 pixel에서만 수행된다. 따라서 관측 영역에서 오차가 작더라도, 정작 LiDAR가 관측하지 못한 영역의 예측 depth가 정확하다는 보장은 없다.

2. **Patch 내 minimum depth 선택은 foreground 편향과 outlier에 취약하다.**  
   LiDAR point가 전혀 없는 patch에서는 filtering을 통과한 completion depth 중 가장 작은 값을 대표 point로 선택한다. 이는 가까운 foreground를 우선 확보하려는 heuristic이지만, 작은 depth로 잘못 예측된 outlier가 존재하면 그 값을 그대로 선택한다. 또한 completion confidence나 uncertainty를 별도로 사용하지 않는다.

3. **하나의 LiDAR depth만 있어도 patch 전체를 completion 대상에서 제외한다.**  
   공개 코드에서는 patch 내부에 유효한 sparse LiDAR depth가 하나라도 존재하면 해당 patch를 건너뛴다. 따라서 patch 대부분이 비어 있더라도 일부 LiDAR 관측만으로 completion point 생성이 억제되어, 실제 미관측 영역을 충분히 보완하지 못할 수 있다.

4. **논문과 공개 설정 사이에도 차이가 있다.**  
   논문은 \(30\times30\) patch와 최대 depth threshold \(\epsilon_2=50\,\mathrm{m}\)를 기술하지만, 공개된 주요 configuration은 `patch_size: 10`, `max_depth: 20`을 사용한다. 따라서 논문에 보고된 결과를 공개 코드의 기본 설정으로 재현할 때 차이가 발생할 가능성이 있다.

5. **Depth completion 자체의 효과를 분리한 정량적 ablation이 부족하다.**  
   논문은 completion 적용 전후를 시각적으로 비교하지만, depth completion module만 제거한 정량적 ablation은 명확히 제시하지 않는다. `Ours-2-w/o-d`는 rendering optimization의 depth supervision을 제거한 설정으로, SPNet depth completion을 제거한 실험과는 다르다.

결국 Gaussian-LIC2의 핵심 기여는 LiDAR blind area를 learned depth로 채워 Gaussian map의 coverage를 넓히는 것이지만, **직접 관측되지 않은 영역의 depth를 검증하지 않은 채 단일 예측값으로 3D Gaussian을 생성한다는 점**이 핵심적인 취약점이다. 잘못 생성된 Gaussian은 이후 RGB rendering loss로 수정될 수 있으나, texture가 부족하거나 view가 제한된 영역에서는 잘못된 geometry가 유지될 가능성이 있다.

근거: [Gaussian-LIC2 공개 구현](https://github.com/APRIL-ZJU/Gaussian-LIC/blob/master/src/gaussian.cpp), [공개 설정 파일](https://github.com/APRIL-ZJU/Gaussian-LIC/blob/master/config/fastlivo2.yaml), [Gaussian-LIC2 논문](https://arxiv.org/html/2507.04004v2)


# 내가 생각한 문제점 과 아이디어 정리
- LIC1 > Visual SfM point도 sparse한데 더 잘 할 수는 없나?
   - 그래서 LIC2에서 SPNet으로 dense depth map을 만들고, 그 중에서도 필요한 부분에만 point를 더 생성
      - 잘 되는지에 대한 검증이 필요함
      - 성능은 올랐다. 근데 Sliding Window Optimization때문인지, 이것때문인지 모름
- Pose Refinement의 부재
   - Coco-LIC를 많이 믿는것인지, Gaussian LIC1은 이후의 pose refinement를 수행하지 않음.
   - LIC2의 option2에서 Gaussian map을 고정한 뒤 Pose를 refinement 하게되어있음. 근데 코드가..?

## IDEA
1. 빠르게 Pose를 refienment를 하려면?
   - IESKF
   - KF
2. 더 의미있는 초기화를 하려면?
   - Visual point > Depth completion > Feed-Forward network?
   - 초기 Scale을 결정할 때 depth와 f로 나누는게 맞나?
      - plane/edge/Cylinder 에 따라 다르게 해야하는것 아닌가?
   