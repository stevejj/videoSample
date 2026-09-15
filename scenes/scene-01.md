# Scene 1 (0~8초) — "분리수거 한 번에 다 들고 나가기"

## 컨셉
- 장르/톤: 일상 공감 개그
- 등장: 팽창수 단독 (팽미순 미등장)
- 배경: 평범한 신혼부부 집 현관
- 상황: 남편이 재활용품을 한 번에 다 들고 나가려는 모습. "남편들은 왜 분리수거를 한 번에 다 버리려고 할까" 공감 포인트.
- 결말: 씬 자체 완결형 — 위태롭게 휘청이지만 넘어뜨리거나 쏟지 않고 힘겹게 문밖으로 잘 들고 나가는 데 성공.
- 과장 수준: 현실적으로 조금 많은 정도

## 소품 (시작/끝 프레임 동일하게 유지)
1. 끈으로 묶은 납작한 종이박스 묶음 — 한쪽 날개 옆구리에 낌
2. 투명 비닐봉지에 담긴 빈 페트병 — 반대쪽 날개로 쥠
3. 캔이 담긴 망사백 — 종이박스 묶음 위에 걸침

## 상태
- [x] 컨셉 확정
- [x] 시작/끝 프레임 프롬프트 초안 작성 + 자체 검증 통과
- [x] 1차 시도 결과 시작/끝 프레임 배경 불일치 발견 → 끝 프레임을 "시작 프레임 이미지 기반 편집" 방식으로 수정 (배경 유지 확인됨)
- [x] 외형 임의 변경 금지 / 의상 임의 추가 금지 제약 조건 추가 → v3로 재작성
- [x] v3 시작 프레임 결과 확인 → 눈썹이 생기고 눈 크기/모양 변형됨 (원인 추정: "furrowed brow" 표현이 눈썹으로 해석됨) → FACE LOCK 블록 추가, 해당 표현 제거 → v4로 재작성
- [x] v4 시작 프레임 결과 확인 → 성공 (눈썹 없음, 눈 크기 정상, 외형/의상/소품 모두 조건 충족)
- [x] 캐릭터 크기가 문/신발장 대비 다소 큰 편(사람 몸통만한 크기)인 점 확인 — 숏폼 특성상 문제없다고 판단, 크기 앵커 문구 추가 없이 현재 상태로 진행하기로 결정
- [x] 끝 프레임 v4 결과 확인 → 실패. 문도 안 열리고 포즈도 거의 그대로라 시작 프레임과 사실상 동일 → "변화 요청"을 최상단에 강조하는 구조로 v5 재작성
- [x] 끝 프레임 v5 결과 확인 → 부분 성공. 문은 열렸지만(성공) 캐릭터 위치/기울임은 여전히 거의 그대로(실패) → 요구사항을 "이동"이라는 단일 핵심 변화로 좁히고, v5 결과물(문 열림)을 새 베이스로 삼아 v6 재작성
- [x] 끝 프레임 v6 결과 확인 → 실패. 문이 더 열리긴 했으나 캐릭터 위치는 또 그대로 → **접근 방식 자체를 "제자리 이동" → "카메라 줌인/거리 변화"로 전환**하여 v7 재작성 (아래 "위치 이동 대신 카메라 거리 변화" 참고)
- [ ] 끝 프레임을 v7 프롬프트로 재생성 (캐릭터 참조 + v6 결과물 2장 첨부)
- [ ] 영상 연결 프롬프트(Veo 3.1 Lite)는 이미지 결과 확인 후 결정

## ① 시작 프레임 (나노바나나 프롬프트, v4)
```
Using the uploaded reference image of the fluffy 3D pixar-style baby penguin
character Paeng Chang-su (no accessory), generate a vertical 9:16 image.

Setting: the entryway of an ordinary newlywed couple's home — a small shoe
rack against the wall, the front door in the background, a simple doormat,
soft warm indoor lighting, plain and unremarkable interior colors.

Chang-su stands in the middle of the entryway, about to head out. He is
carrying all his recycling in one trip: a flat bundle of tied cardboard
boxes held under one wing-flipper against his side, a clear plastic bag
full of empty PET bottles gripped by the other wing-flipper, and a small
mesh bag of aluminum cans hooked on top of the cardboard bundle. He leans
slightly forward, torso tilted to counterbalance the load, one foot
stepping toward the door.

His expression stays calm and natural, with only the mild physical effort
of carrying a heavy load — subtle, NOT exaggerated or cartoonish.

Camera: medium-full shot, eye-level, slight 3/4 angle toward the door.
Soft, warm, realistic indoor lighting.

FACE LOCK (highest priority, do not deviate):
- The face must exactly match the reference image: large, round, wide-set
  eyes that take up a big portion of the face, each with one bright round
  catchlight, dark eye color, no visible pupils narrowing or squinting.
- NO eyebrows of any kind. The character has smooth dark head fur directly
  above the eyes with nothing resembling an eyebrow shape, line, or
  furrow. Do not draw any brow markings.
- Keep the exact same round head shape, face proportions, orange beak
  shape and size, and fur coloring as the reference image. Do not narrow,
  elongate, or reshape the eyes or face in any way.

OTHER CONSTRAINTS:
- Do not alter Chang-su's body proportions, colors, or fur texture from
  the reference image.
- Do not add any clothing, costume, accessories, or props on his body
  unless explicitly described above. He stays exactly as unclothed/bare as
  in the reference image — no shirt, no scarf, no hat, nothing extra.
- No text, no logos, no watermark.
```

## ② 끝 프레임 (나노바나나 프롬프트, v7)
> **접근 전환**: v4~v6까지 "같은 구도 유지 + 캐릭터 위치만 이동"을 계속 요청했지만 매번 위치가 거의 안 바뀌었음. 카메라가 문(바깥) 방향에서 그를 바라보는 구도라, "문밖으로 나간다"는 사실상 "카메라 쪽으로 가까워진다"는 뜻인데, 모델이 "배경/구도 유지" 지시를 픽셀 단위로 지키려다 보니 인물 이동 자체를 무시하는 패턴이 반복됨. 그래서 "제자리에서 옮겨라"가 아니라 **"카메라는 그대로, 그가 다가와서 화면에 더 크게 잡힌다"는 줌인/프레이밍 변화**로 요청 방식을 바꿈.
> **첨부**: 캐릭터 참조 이미지 + v6 결과물(문 많이 열린 이미지)을 베이스로 첨부

```
Using the second reference image (the latest attempt photo) as the base
for character identity, colors, and style — but this is a full
recomposition of the shot, not a small pixel-level edit.

REQUIRED CHANGE — CAMERA PUSH-IN (the single most important change):
Chang-su has walked forward through the doorway and is now much closer to
the camera than in the base image, as if the camera stayed in place while
he approached it. He must appear noticeably larger in the frame — roughly
25-35% bigger/taller than in the base image. Because he is closer to
camera: the top of the door frame is now partially cropped out of frame or
only visible at the very top edge, and the shoe rack on the side is now
mostly or fully out of frame (he has walked past it). This must be an
unmistakable, obvious change in framing and scale compared to the base
image — NOT the same wide shot with him standing in the same spot.

His body is tilted/leaning to counterbalance the load, mid-stride, a
natural subtle wobble. NOT exaggerated or cartoonish.

KEEP THE SAME STYLE as the base image:
- Same three recycling items in the same positions: tied cardboard bundle
  under one wing-flipper, clear bag of PET bottles in the other
  wing-flipper, mesh bag of cans hooked on top of the cardboard bundle.
- Same lighting mood, color tone, and character colors/fur texture.
- Whatever entryway/hallway background is now visible at this closer
  camera distance should still look consistent with the same home.

Expression: natural and understated, a touch more visible effort than the
base image. Subtle, NOT exaggerated or cartoonish.

FACE LOCK (highest priority, do not deviate):
- The face must exactly match the reference images: large, round,
  wide-set eyes that take up a big portion of the face, each with one
  bright round catchlight, dark eye color.
- NO eyebrows of any kind. Smooth dark head fur directly above the eyes,
  nothing resembling an eyebrow shape, line, or furrow.
- Keep the exact same round head shape, face proportions, orange beak
  shape and size, and fur coloring as the reference images.

OTHER CONSTRAINTS:
- Do not alter Chang-su's body proportions, colors, or fur texture from
  the reference images.
- Do not add any clothing, costume, accessories, or props on his body
  beyond the three recycling items already described.
- No text, no logos, no watermark.
```

---

## 히스토리 (참고용, 이전 버전)

### v6 (끝 프레임) — 단일 요구("이동"만)로 좁혔지만 여전히 실패
- 결과: 문은 더 열렸지만 캐릭터 위치는 또 그대로. "제자리 이동" 요청 자체가 이 구도(카메라가 문/바깥 방향에서 그를 바라봄)에서는 잘 안 통하는 것으로 판단.
- 교훈: 아래 "위치 이동 대신 카메라 거리 변화" 참고 → v7에서 접근 전환.

### v5 (끝 프레임) — REQUIRED CHANGES 리스트 3개 → 1개만 반영됨
- 결과: 문 열림은 성공, 하지만 캐릭터 이동/기울임은 여전히 거의 반영 안 됨.
- 원인 추정: 요구 변화가 3가지(문/이동/기울임)로 분산되면서 모델이 그중 상대적으로 "쉬운" 변화(문 열기)만 확실히 반영하고 "어려운" 변화(포즈·위치 이동)는 소극적으로 처리한 것으로 보임.
- 교훈: 요구 변화를 **하나로 좁히고**, 이미 성공한 변화(문 열림)는 새 베이스 이미지 자체에 반영시켜 재확인 요구를 줄이는 게 효과적. "위치가 한눈에 확실히 다르게 보여야 한다"처럼 변화의 크기/기준을 구체적으로 명시.

### v4 (끝 프레임) — "베이스 유지 + 살짝 편집" 구조 → 변화가 거의 반영 안 됨
- 결과: 문이 안 열리고, 캐릭터 위치/자세도 시작 프레임과 거의 동일. 시작·끝 프레임이 사실상 같은 사진.
- 원인 추정: "keep the same background... edit only the character"처럼 **"유지" 지시를 먼저, "변화" 지시를 나중에** 배치하면 모델이 유지 쪽에 더 무게를 둠.
- 교훈: **"반드시 바뀌어야 할 것"을 프롬프트 최상단에 명확한 리스트로 강조**하고, "이건 베이스 이미지와 거의 동일한 반복이 아니다"라고 명시적으로 못박을 것. "유지할 것" 목록은 그다음 순서로 배치.

### v3 — 추상적 금지 문구("Do not alter appearance")만 사용 → 실패
- 결과: 눈썹이 생기고 눈이 작아짐/좁아짐. "a slightly furrowed brow" 표현이 원인으로 추정(브로우=눈썹 연상).
- 교훈: 추상적 금지보다 **구체적으로 없어야 할 것(NO eyebrows 등)과 정확한 비율/형태**를 명시하는 FACE LOCK 블록이 필요. "brow", "furrow" 등 눈썹을 연상시키는 단어는 표정 묘사에서 피할 것.
- 전체 텍스트는 위 대화 기록 참고 (구조는 v4와 동일하되 FACE LOCK 블록 없음).

### v1 — 끝 프레임을 캐릭터 참조만으로 새로 생성 → 배경이 어긋남
```
Using the same reference image of Paeng Chang-su, generate a vertical 9:16
image continuing the same moment, a few steps later.

Same setting: the entryway, now with the front door open and Chang-su just
stepping over the threshold, one foot past the doorway. He is still
carrying the exact same three items as before, in the same positions: the
tied cardboard bundle under one wing-flipper, the clear bag of PET bottles
in the other wing-flipper, and the mesh bag of cans hooked on top of the
cardboard bundle — nothing added, nothing dropped.

His body is tilted a bit further off-balance than before, wobbling
slightly to keep everything steady, but he is clearly managing it without
anything slipping. His expression stays natural and understated — a touch
of strain mixed with the beginning of relief. NOT exaggerated or
cartoonish.

Camera: same medium-full shot, same eye-level 3/4 angle, same soft warm
lighting as the start frame, doorway now open with a hint of outdoor
light/scenery beyond it. Same fluffy fur texture, proportions, and colors
as the reference image. No text, no logos, no watermark.
```

### v2 — 시작 프레임을 참조로 편집 → 배경 유지 성공, 외형/의상 제약 조건은 없었음
```
Using the second reference image (the start frame photo) as the exact base
— keep the same background, same entryway layout, same camera angle, same
lighting, same color tone — edit only the character. Chang-su has now
stepped further forward, one foot past the doorway, front door open. He is
still carrying the exact same three items as before, in the same
positions: the tied cardboard bundle under one wing-flipper, the clear bag
of PET bottles in the other wing-flipper, and the mesh bag of cans hooked
on top of the cardboard bundle — nothing added, nothing dropped.

His body is tilted a bit further off-balance than before, wobbling
slightly to keep everything steady, but he is clearly managing it without
anything slipping. His expression stays natural and understated — a touch
of strain mixed with the beginning of relief. NOT exaggerated or
cartoonish.

Do not change anything else in the scene — same fluffy fur texture,
proportions, and colors as the character reference image. No text, no
logos, no watermark.
```

## ③ 영상 연결 프롬프트 (Veo 3.1 Lite)
- 이미지 생성 결과 확인 후 결정 예정
