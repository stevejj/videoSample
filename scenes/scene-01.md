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
- [x] 끝 프레임 v7 결과 확인 → 카메라 줌인/프레이밍 변화 자체는 성공(캐릭터 확대, 문/신발장 크롭됨). 하지만 **사용자 피드백으로 반려**: "나간다"는 서사를 줌인으로 대체하면 안 됨 — 캐릭터의 실제 이동/자세 변화로 표현해야 함. 접근 전환을 되돌리고, 카메라/줌은 완전히 고정한 채 **다리·발 위치를 문자 그대로 지정하는 구체적 포즈 묘사**로 v8 재작성
- [x] v8 시도 전, 사용자가 구도 자체의 물리적 모순을 지적(문이 배경에 있으니 "정면 유지+전진"은 뒷걸음질을 요구하는 셈) → **뒷모습(back view)으로 전환**하여 v9 작성. v8은 시도하지 않고 폐기.
- [x] 끝 프레임 v9 결과 확인 → 성공. 뒷모습 전환, 문 열림, 문턱 근처 위치, 배경/소품 일관성 모두 확인됨. **시작/끝 프레임 최종 확정.**
- [x] 영상 연결 프롬프트(Veo 3.1 Lite) 컨셉 제안 → 사용자 승인(BGM 잔잔 + 효과음만, 대사/텍스트 없음) → v1 프롬프트 작성 완료
- [x] v1 영상 결과를 2fps로 프레임 분석 → 문 열림/닫힘 반복, 제자리걸음(실제 이동 없음), 소품(종이박스) 깜빡임 3가지 문제 발견 → "절대 하면 안 되는 것"을 명시하는 CRITICAL RULES 추가해 v2로 재작성
- [x] 사용자 피드백: 끝 프레임(v9)이 "문턱 근처"까지만이라 도착점이 약해서 영상이 끝까지 자연스럽게 안 이어짐 → 끝 프레임을 **완전히 문 밖으로 나가 바깥에 선 모습**으로 v10 재작성
- [x] v10 시도 전, 사용자가 v9(=v10의 베이스) 자체의 물리 오류를 지적: 뒤돌았는데 소품 좌우가 정면일 때와 동일하게 유지됨(180도 회전이면 좌우가 바뀌어야 함) → 좌우 교정 지시를 추가해 v11로 재작성. v10은 시도하지 않고 폐기.
- [x] 끝 프레임 v11 결과 확인 → 실패. 좌우 교정 지시를 명시했는데도 소품 위치가 그대로임(v9 베이스 이미지의 레이아웃에 앵커링된 것으로 추정) → **베이스를 v9가 아니라 확정된 시작 프레임(정면, 올바른 좌우)으로 되돌려서** 처음부터 다시 생성하는 방식으로 v12 재작성
- [x] 끝 프레임 v12 결과 확인 → 부분 실패. 좌우 여전히 안 바뀜(시작 프레임 베이스로 되돌려도 실패), "완전히 바깥으로 나감"도 미반영, 문턱 근처에서 또 멈춤 → 우선순위 분리: 거리는 "단일 요청 집중" 전략, 좌우는 "미러/flip" 개념으로 재시도하는 v13 작성
- [ ] 끝 프레임을 v13 프롬프트로 재생성 후 결과 확인
- [ ] **끝 프레임이 v10으로 바뀌면 영상 연결 프롬프트도 재조정 필요** (v2는 "문턱에서 멈춤"이 도착점이었는데, v10은 "완전히 바깥으로 나감"이 도착점이므로 이에 맞게 다시 써야 함)

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

## ② 끝 프레임 (나노바나나 프롬프트, v13)
> **v12 결과도 부분 실패(사용자 확인)**: 시작 프레임으로 베이스를 되돌렸는데도 좌우 여전히 안 바뀜, 그리고 "완전히 바깥으로 나감"도 반영 안 되고 문턱 근처에서 또 멈춤. **우선순위 분리**: (1) 거리(바깥으로 나감)는 예전에 성공했던 "단일 요청 집중" 전략으로 v12 결과물을 베이스로 재시도. (2) 좌우는 "물리적 설명"이 아니라 "미러/좌우반전(flip)"이라는 이미지 편집 개념으로 재시도. 이마저 안 되면 좌우는 포기하고 거리만 확정.
> **첨부**: 캐릭터 참조 이미지 + **v12 결과물**(뒷모습, 문턱)을 베이스로 사용

```
Using the second reference image (the latest photo) as the base — this is
a full new photograph of a later moment, from the exact same fixed camera
position.

REQUIRED CHANGE (the single most important change — must be large and
unmistakable): Chang-su has walked further away from the camera, out
through the doorway, and is now standing outside on the outdoor landing.
He must appear noticeably smaller in the frame than in the base image —
roughly half his current height — with the door frame taking up much more
of the surrounding image, and more outdoor scenery (sky, railing,
neighboring building, ground) visible around him. This must be an
unmistakable distance change, not a subtle one.

SECONDARY CHANGE — MIRROR THE ITEM ARRANGEMENT: The item arrangement in
this new image must be a left-right MIRROR (horizontal flip) of the base
image. Whatever item is on screen-LEFT in the base image must be on
screen-RIGHT in this new image, and whatever is on screen-RIGHT in the
base image must be on screen-LEFT in this new image. Treat this as a
horizontal-flip transform of the item layout, not a copy.

Still seen from BEHIND, same character colors/fur texture, same two
recycling items (cardboard-and-cans bundle, PET bottle bag) — nothing
added or dropped, just repositioned per the mirror instruction above.

His body is upright and steady — task accomplished, no wobble.

KEEP IDENTICAL: camera position (fixed), overall lighting mood, color
tone, character's fur colors/texture.

OTHER CONSTRAINTS: no clothing/accessories added, no text/logo/watermark.
```

---

## 히스토리 (참고용, 이전 버전)

### v12 (끝 프레임) — 시작 프레임으로 베이스 리셋 → 좌우/거리 둘 다 여전히 실패
- 결과: 베이스를 시작 프레임(정면, 올바른 좌우)으로 되돌리고 처음부터 다시 생성했는데도, 좌우는 정면과 동일하게 유지되고, "완전히 바깥으로 나감"도 반영 안 되어 문턱 근처에서 멈춤. 즉 v9(뒷모습 성공)와 사실상 거의 동일한 결과.
- 교훈: 좌우 반전은 베이스를 바꿔도(v9 기반이든 시작 프레임 기반이든) 3번 연속 실패 → 나노바나나의 구조적 한계일 가능성이 높음. "물리적으로 설명"하는 방식(어느 날개인지, 왜 바뀌는지)이 잘 안 먹히므로, 다음엔 "미러/좌우반전(flip)"이라는 순수 이미지 편집 개념으로 재시도(v13). 거리 문제도 "정면 베이스에서 한 번에 다 바꾸기"보다, 예전에 성공했던 "직전 결과물을 베이스로 단일 변화만 강하게 요청"하는 방식으로 되돌아감.
- 프롬프트 전체 텍스트: 위 v13 항목의 "v12 결과도 부분 실패..." 참고, 또는 이전 대화 기록 참고.

### v11 (끝 프레임) — v9를 베이스로 좌우 교정 지시 → 반영 안 됨
- 결과: "화면 좌우가 바뀌어야 한다"고 명시적으로 설명했는데도 소품 위치가 v9와 동일하게 유지됨.
- 교훈: 이미 틀린 이미지를 베이스로 주고 "이 부분만 고쳐라"고 하면, 모델이 베이스 이미지의 기존 레이아웃에 강하게 앵커링되어 텍스트 교정 지시를 무시하는 경향이 있음(앞서 "제자리 이동" 실패와 유사한 패턴). **틀린 결과물을 계속 베이스로 재사용하며 고치려 하지 말고, 마지막으로 올바르다고 확인된 이미지(여기선 시작 프레임)로 베이스를 되돌려서 처음부터 다시 생성**하는 게 더 효과적 → v12.
- 프롬프트 전체 텍스트: 위 v12 항목의 "v11 결과도 실패..." 참고, 또는 이전 대화 기록 참고.

### v9 (끝 프레임) — 뒷모습 전환 자체는 성공했으나 "문턱 근처"라 도착점이 약함
- 결과: 뒷모습, 문 열림, 배경/소품 일관성 모두 확인되어 한때 "최종 확정"으로 기록했으나, 실제 영상(Veo) 생성 결과가 8초 안에 이 애매한 종착점까지도 제대로 못 이어가는 문제(문 열림/닫힘 반복, 제자리걸음)로 이어짐.
- 교훈: 끝 프레임이 "얼추 도착"이 아니라 **명확하게 완료된 상태**(완전히 문 밖으로 나감)여야 영상 모델이 갈 방향을 더 뚜렷하게 잡음. 프레임 단위 검증 통과 ≠ 실제 영상화까지 잘 됨 — 영상 생성 결과까지 보고 나서 최종 확정해야 함.
- 프롬프트 전체 텍스트: 위 v10 항목의 "v9 결과 자체는 반영됐으나..." 참고, 또는 이전 대화 기록 참고.

### v8 (끝 프레임) — 시도 전 폐기. 구도(카메라-캐릭터-문 배치) 자체가 잘못됨을 사용자가 지적
- 문이 배경(캐릭터 뒤)에 있는 구도이므로, "정면 유지한 채 앞으로 이동"은 애초에 물리적으로 맞지 않는 요청이었음(정면 유지하려면 뒷걸음질쳐야 함). v9에서 뒷모습으로 전환.

### v7 (끝 프레임) — 카메라 줌인으로 대체 → 구도 변화는 성공했으나 서사상 반려
- 결과: 캐릭터가 확대되고 문/신발장이 크롭되어 "가까워짐"은 시각적으로 성공. 하지만 포즈 자체는 거의 그대로(제자리 서있는 자세 확대일 뿐), 그리고 사용자가 "이건 실제 이동이 아니라 카메라 트릭이라 서사에 안 맞는다"고 반려.
- 교훈: 기술적으로 더 잘 먹히는 방법이라도 스토리 의도와 안 맞으면 채택하면 안 됨. **카메라 고정 + 실제 포즈/이동 변화**를 계속 시도하는 게 맞고, 대신 포즈 묘사를 훨씬 더 구체적으로(다리/발 위치 단위) 써야 함 → v8.
- README `제작 가이드라인`의 "위치 이동 대신 카메라 거리 변화" 항목은 **사용 보류**(기술적으로는 유효하지만 이 프로젝트의 서사 원칙과 충돌할 수 있어 케이스별로 판단 필요).

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

## ③ 영상 연결 프롬프트 (Veo 3.1 Lite, v2)
> **컨셉**: 문 닫힘 상태로 정면 서있음 → 몸으로 문 밀어 열기 → 뒤돌아서 문 쪽으로 걸어감(휘청이며 균형 잡음) → 문턱 근처에서 안정적으로 멈춤(끝 프레임과 매칭). 카메라 완전 고정, 대사/텍스트 없음, 잔잔한 배경음악 + 효과음만.
> **v1 결과 분석(2fps 프레임 분석)**: (1) 문이 열렸다(1.5~4.5초)→거의 닫힘(5.0~5.5초)→다시 열림(6.0초~) 하며 왔다갔다함. (2) 3.0초에 뒤돈 이후 8초 끝까지 같은 자리에서 제자리걸음만 하고 실제 이동이 없음. (3) 4.0초에 종이박스 묶음이 사라졌다가 4.5초에 재등장. → 원인: 여러 단계(문 열기+뒤돌기+걷기+휘청임+멈춤)를 한 번에 요청한 게 Lite 모델엔 과했던 것으로 추정. v2는 "절대 하면 안 되는 것"을 명시적으로 못박아 단순화.

```
An 8-second continuous shot, camera completely static — no panning, no
zooming, no cuts — fixed in the entryway of an ordinary home.

Chang-su, a small fluffy 3D-pixar-style penguin character, starts facing
the camera, holding a heavy load of recycling: a tied cardboard bundle
with a mesh bag of cans hooked to it in one wing-flipper, a clear bag of
PET bottles in the other. The front door in front of him is closed.

In one single continuous motion, with no pauses, no reversals, and no
repeated actions: he turns around away from the camera, pushing the door
open with his body as he turns, and immediately begins walking steadily
toward the open doorway. He keeps moving forward for the entire remainder
of the clip, getting closer to the doorway with every second, until he
reaches the threshold at the very end.

CRITICAL RULES (do not violate these):
- The door opens exactly once, early in the clip, and then stays open for
  the rest of the video. It must never close again, even partially, at
  any point after it opens.
- Chang-su moves continuously forward toward the door for the entire
  clip. He must never stand still, walk in place, or move backward —
  there must be clear, steady progress toward the doorway in every second
  of footage, from start to finish.
- The two items (the cardboard-and-cans bundle, the PET bottle bag) stay
  solid and continuously visible the entire time. They must not flicker,
  disappear, change shape, or change which item is which.
- Do not repeat, loop, hesitate, or reverse any part of the motion.

His body leans/wobbles slightly side to side as he walks, working to keep
his balance under the load — a natural, subtle wobble, not exaggerated.
He never drops or spills anything.

Motion should be natural and continuous, not exaggerated or cartoonish.

Audio: gentle, soft background music throughout (calm, warm, understated
mood). Light, realistic sound effects only — a door creak/click as it
opens, soft footsteps, a faint rustle of the plastic bag and clinking
cans. NO dialogue, NO voiceover, NO on-screen text or captions.
```

### v1 (참고용, 폐기)
```
An 8-second continuous shot, camera completely static — no panning, no
zooming, no cuts — fixed in the entryway of an ordinary home.

Chang-su, a small fluffy 3D-pixar-style penguin character, stands facing
the camera holding a heavy load of recycling: a tied cardboard bundle with
a mesh bag of cans hooked to it in one wing-flipper, and a clear bag of
PET bottles in the other. The front door in front of him is closed.

He nudges the door open with his body/shoulder since both wings are full,
struggling slightly. As the door swings open, he turns fully around, away
from the camera, and begins walking toward the now-open doorway, his back
now to the camera. He walks with a subtle side-to-side wobble, visibly
working to keep his balance under the load, but never drops or spills
anything. He reaches the doorway threshold and comes to a steady stop,
standing just at the open door with the outside visible beyond it.

Motion should be natural and continuous, not exaggerated or cartoonish —
a believable, slightly effortful walk, not a comedic pratfall.

Audio: gentle, soft background music throughout (calm, warm, understated
mood). Light, realistic sound effects only — a door creak/click as it
opens, soft footsteps, a faint rustle of the plastic bag and clinking
cans. NO dialogue, NO voiceover, NO on-screen text or captions.
```
