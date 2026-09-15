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
- [ ] 끝 프레임을 v4 프롬프트로 생성 (캐릭터 참조 + 확정된 시작 프레임 이미지 2장 첨부)
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

## ② 끝 프레임 (나노바나나 프롬프트, v4)
> **첨부**: 캐릭터 참조 이미지 + 방금 생성된 시작 프레임 이미지, 총 2장을 함께 참조로 첨부할 것 (배경 어긋남 방지).

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
anything slipping. His expression stays natural and understated, with a
touch more visible effort than the start frame — subtle, NOT exaggerated
or cartoonish.

FACE LOCK (highest priority, do not deviate):
- The face must exactly match the reference images: large, round,
  wide-set eyes that take up a big portion of the face, each with one
  bright round catchlight, dark eye color.
- NO eyebrows of any kind. The character has smooth dark head fur directly
  above the eyes with nothing resembling an eyebrow shape, line, or
  furrow. Do not draw any brow markings.
- Keep the exact same round head shape, face proportions, orange beak
  shape and size, and fur coloring as the reference images. Do not narrow,
  elongate, or reshape the eyes or face in any way.

OTHER CONSTRAINTS:
- Do not alter Chang-su's body proportions, colors, or fur texture from
  the reference images.
- Do not add any clothing, costume, accessories, or props on his body
  beyond the three recycling items already described. He stays exactly as
  unclothed/bare as in the reference images — no shirt, no scarf, no hat,
  nothing extra.
- Do not change anything else in the scene (background, layout, lighting,
  camera angle, color tone).
- No text, no logos, no watermark.
```

---

## 히스토리 (참고용, 이전 버전)

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
