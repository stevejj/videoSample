# Scene 1 (0~8초) — "분리수거 한 번에 다 들고 나가기"

## 컨셉
- 장르/톤: 일상 공감 개그
- 등장: 팽창수 단독 (팽미순 미등장)
- 배경: 평범한 신혼부부 집 현관
- 상황: 남편이 재활용품을 한 번에 다 들고 나가려는 모습. "남편들은 왜 분리수거를 한 번에 다 버리려고 할까" 공감 포인트.
- 결말(v16 업데이트): 씬 자체 완결형 — 위태롭게 휘청이지만 넘어뜨리거나 쏟지 않고 힘겹게 문밖으로 잘 들고 나간 뒤, **문을 닫고 완전히 퇴장** → 끝 프레임은 캐릭터 없는 빈 현관(문 닫힘)으로 마무리.
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
- [x] 끝 프레임 v13 결과 확인 → 좌우 문제 지속(사용자 확인). 4번째 접근도 실패 → 이전 생성물을 베이스로 쓰는 것 자체가 원인일 수 있다고 판단, **최초 턴어라운드 시트(뒷모습 포함)만 참조해 이전 생성물 없이 완전히 새로 생성**하는 v14 작성
- [x] v14 시도 전, 사용자가 영상 결과를 보고 방향 전환: 좌우 반전은 억지로 맞추지 않아도 될 것 같다고 판단 → **"확실히 밖으로 나가있기"에만 집중**하고 소품 "배치 유지" 문구도 제거한 v15로 재작성. v14는 시도하지 않고 폐기.
- [x] 끝 프레임 v15 결과 확인 → 거리(확실히 밖으로 나가있음, 난간/옆 건물까지 보임) 성공. 소품 좌우는 나노바나나 프롬프트로는 끝내 실패했지만, **Flow 자체의 영역 지정 좌우 교체 기능으로 사용자가 직접 수정**하여 해결. **시작/끝 프레임 최종 확정.**
- [x] 영상 연결 프롬프트(Veo 3.1 Lite) v3 작성 — 최종 확정된 끝 프레임(더 멀리 나간 버전)에 맞춰 이동 거리 조정
- [x] 사용자 요청으로 컨셉 대전환: 끝 프레임을 **캐릭터 없는 빈 현관(문 닫힘)**으로 변경 → 좌우/거리 문제 자체가 무의미해짐. v16 작성.
- [ ] 끝 프레임을 v16 프롬프트로 재생성 후 결과 확인
- [x] 영상 연결 프롬프트를 v16 결말(문 닫힘)에 맞춰 v4로 재작성 — 등으로 문 밀기 + 도어클로저로 자동으로 문 닫힘 컨셉 반영
- [x] v5 영상 결과를 2fps로 프레임 분석 → 심각한 렌더링 붕괴 다수 발견. 처음엔 "단계가 너무 많다"고 판단했으나, 사용자 지적으로 재검토하여 **구체적 원인 3가지**를 찾음: (1) "turns toward screen-RIGHT"의 "turns"가 몸 재회전으로 오독됨, (2) 문이 열린 상태의 참조 이미지가 없어서 디자인이 매번 다르게 그려짐, (3) 문 닫힘 타이밍이 캐릭터 퇴장과 연동 안 됨. 세 가지 다 교정하여 v6 재작성.
- [x] v6 시도 전, 사용자가 두 가지 추가 지적: 문이 바깥쪽으로 열려야 함(안쪽으로 열리는 것처럼 보임), 문 밖 풍경에 "문처럼 생긴 구조물"이 또 보여서 어색함 → 문이 바깥으로 열리고, 문 밖은 순수 야외 배경만 보이도록 명시하는 v7 재작성
- [x] v7 시도 전, 사용자가 "등으로 힘겹게 밀어서 여는 것"이 씬의 핵심 포인트인데 다른 규칙들 사이에 묻혔다고 지적 → 이 동작을 프롬프트 최상단에 "MOST IMPORTANT MOMENT"로 분리하고 구체적 신체 동작으로 생생하게 묘사하는 v8 재작성
- [x] v8 실제 테스트 전, 스토리보드 그리드(나노바나나, 무료)로 먼저 동작을 검증하기로 방향 전환 → 그리드 v1~v5 반복하며 0~7초 전 구간 확정 (관용구 회피, 매초 제약 반복+요약 규칙, 긍정+부정 제약 페어 등 교훈 발견 및 스킬에 반영)
- [x] 확정된 스토리보드 그리드의 초 단위 내용을 그대로 옮겨서 영상 프롬프트 v9 작성
- [x] v9 영상 결과를 2fps로 프레임 분석 → 최종 상태(문 닫힘/빈 방)는 정확했지만, 문 미는 동작에 시간을 너무 많이 써서(0~4초) 캐릭터가 거의 안 움직이다가 5.5~6초에 급하게 이동을 몰아 처리하며 옆모습 노출 글리치 발생 → 문 미는 구간에 절대 시간 상한 명시, 2~6초 구간에 "매초 이동 필수" 규칙 추가한 v10 재작성
- [x] v10 시도 전, 사용자가 물리적 모순 지적: "뒤돌아서 등으로 민다"는 뒤돈 순간 정면이 문을 향하게 되어 등으로 미는 게 불가능한 지시였음 → 뒤돌기를 미는 동작 뒤(3초)로 옮기고, 미는 동안엔 정면을 유지한 채 뒷걸음질로 등을 대는 구조로 v11 재작성
- [x] v11 영상 결과를 2fps로 프레임 분석 → 몸 방향 논리 자체는 문제없었으나 **실행 타이밍이 드리프트**: (1) "1s-2s 정면 유지"가 지켜지지 않고 1s부터 이미 옆모습으로 돌아가버려 등으로 미는 장면 자체가 제대로 안 잡힘, (2) 3s에 회전은 했지만 3~4.5초 구간이 "매초 이동" 규칙에도 불구하고 거의 정지 상태로 렌더링되어 문턱을 못 넘고 안쪽에 머무름(사용자 피드백과 일치) → 추상적 "매초 이동" 규칙 대신 도어매트/문턱/난간 같은 **구체적 랜드마크에 위치를 고정**하고, 회전 전 구간에 "프로필 금지" 부정 제약을 추가한 v12 재작성
- [x] 사용자가 생성 방식을 "시작/끝 프레임(Frames to Video)"에서 **"소재(Ingredients to Video)"**로 전환 결정 → v12는 테스트 전에 폐기, 참조 이미지 역할을 명시하는 구조로 v13 재작성
- [x] 소재 모드 전환 중 확정 그리드(v5)를 재검토 → **1초 패널이 물리적으로 모순된 구버전 로직("이미 뒤돈 채 등으로 밀기")을 담고 있음을 발견**(v9→v11 사이에 고친 것과 동일 버그). 소재 모드에서는 그리드가 직접 참조 이미지로 들어가 텍스트 지시보다 강하게 작용할 수 있어 위험 → 고쳐진 로직(1s-2s 정면 유지, 3s 1회 회전)에 맞춘 그리드 v6 작성, 재생성 필요
- [ ] 그리드를 v6 프롬프트로 재생성 후 결과 확인
- [ ] 영상을 v13 프롬프트(소재 모드, 참조 이미지 3장: 시작/끝 프레임 + 그리드 v6)로 생성 후 결과 확인

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

## ② 끝 프레임 (나노바나나 프롬프트, v16)
> **컨셉 대전환(사용자 요청)**: 캐릭터가 나가있는 모습 대신, **캐릭터 없는 빈 현관 + 문 닫힘**으로 변경. "문 열고 나가서 다시 닫는다"까지 전체 과정을 8초 영상이 담당하고, 끝 프레임은 그 결과(빈 방)만 보여주는 구조. 좌우 반전/거리 문제 자체가 사라짐.
> **첨부**: 확정된 시작 프레임 이미지 1장 (캐릭터가 없는 장면이라 캐릭터 참조는 불필요)

```
Using the reference image (the confirmed start frame photo) as the exact
base for the room's background, door design, and lighting — generate a
new vertical 9:16 image of the exact same entryway, but completely empty.

THE SCENE: The same home entryway, from the exact same fixed camera
position and framing as the reference image. The front door is closed,
matching the reference image. There is no character in the frame — no
penguin, no recycling items, nothing being carried. Just the empty room.

KEEP IDENTICAL: camera position, entryway layout, shoe rack (with the same
shoes as in the reference image), wall color, door design and color,
doormat, lighting mood, overall color tone — everything exactly as in the
reference image, minus the character.

OTHER CONSTRAINTS: No text, no logos, no watermark. No people, animals, or
characters of any kind in the frame.
```

---

## 히스토리 (참고용, 이전 버전)

### v15 (끝 프레임) — 거리는 성공, 좌우는 Flow 수동 편집으로 해결. 이후 컨셉 자체가 바뀌어 폐기
- 결과: "확실히 밖으로 나가있기"는 성공(난간/옆 건물까지 보임). 소품 좌우는 프롬프트로는 끝내 실패했으나 Flow 자체 편집 툴로 사용자가 직접 수정. 한때 "시작/끝 프레임 최종 확정"으로 기록됨.
- 이후 변경: 사용자가 끝 프레임 컨셉을 아예 바꿔서(캐릭터 없는 빈 현관+문 닫힘) v16으로 재작성. v15는 더 이상 사용하지 않음.
- 프롬프트 전체 텍스트는 위 대화 기록 참고.

### v14 (끝 프레임) — 턴어라운드 시트만으로 새로 생성 (시도 전 폐기)
- 좌우 반전을 여전히 노려서 설계했었으나, 실제 영상 결과를 보고 사용자가 "이 정도면 괜찮다"고 판단 → 좌우는 보류하고 거리(확실히 밖으로 나가있기)에만 집중하는 v15로 방향 전환. v14는 시도하지 않음.
- 참고로 남겨둔 인사이트: 소품에 대해 "same relative arrangement(배치 유지)" 같은 문구를 다른 요구사항(좌우 반전 등)과 함께 쓰면 서로 모순되는 지시가 되어 혼란을 줄 수 있음 — 이후 프롬프트에서는 유지할 필요 없는 속성에 "유지하라"는 말을 넣지 않도록 주의.

### v13 (끝 프레임) — 미러/flip 개념으로 재프레이밍 → 좌우 문제 지속
- 결과: "물리적 설명"에서 "미러/좌우반전"이라는 이미지 편집 용어로 바꿔봤지만 여전히 좌우가 안 바뀜(사용자 확인).
- 교훈: v9→v11→v12→v13 네 번의 서로 다른 접근이 모두 실패. 매번 "직전에 생성된 뒷모습 이미지"를 베이스/참조로 사용했다는 공통점이 있음 — 이게 매번 같은 좌우 배치를 답습하게 만든 근본 원인일 가능성. **이전 생성물 체인을 완전히 끊고, 최초 캐릭터 턴어라운드 시트(실제 뒷모습 레퍼런스 포함)만 사용해 처음부터 새로 생성**하는 방식으로 전환(v14). 이마저 실패하면 모델 한계로 판단하고 포기.
- 프롬프트 전체 텍스트: 위 v14 항목 참고, 또는 이전 대화 기록 참고.

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

## 스토리보드 그리드 프롬프트 (나노바나나, 영상 프롬프트 작성 전 무료 사전 검증)
> **첨부**: 캐릭터 참조 이미지 + 확정된 시작 프레임(v4) + 확정된 끝 프레임(v16), 총 3장, 이 순서로.
> **v1 결과 확인**: 0~4초 흐름은 좋았음. **v2 수정**: 5초에 오른쪽으로 이동하는 게 안 보이고 중앙에 그대로 있었음 → 5초부터 오른쪽으로 각도를 틀며 이동하는 것으로 수정. 6초는 몸이 절반 이상 가려져야 하는데 명시가 부족했음 → "MORE THAN HALF hidden"으로 명시.
> **v3 수정(사용자 요청)**: 5·6·7초가 각각 따로 노는 게 아니라 **하나의 자연스럽게 이어지는 퇴장 동작**으로 읽혀야 함 → 세 컷 사이 전환이 매끄럽게 이어지도록 명시하는 문단 추가.
> **v4 결과 확인(사용자)**: 0~4초는 아주 좋음. 문제 4가지 발견: (1) 2초에 "crack open"(관용구, 문이 빠끔 열리다)을 모델이 문자 그대로 "금이 가다"로 해석해서 문 표면에 균열 텍스처 생김 → "crack" 단어 자체를 빼고 서술. (2) 5초에 뒷모습 유지가 안 되고 갑자기 다시 정면을 봄 → 예전 영상에서도 봤던 패턴("뒷모습 유지"를 매 컷마다 다시 명시 안 하면 리셋됨), 4~6초 각각에 "seen from BEHIND, face NOT visible"을 반복 명시. (3) 3~6초에 소품이 사라짐 → 각 컷에 소품 유지를 반복 명시. (4) 6초에 문이 이미 거의 다 닫혀버림(사용자는 "거의 다 나간 상태"를 원함, 문 닫힘은 아직 아님) → 문이 완전히 닫히는 건 7초에만 일어나도록 타이밍 조정.

```
Using the three reference images — the first is Chang-su's character
reference (for exact face/eye/fur consistency), the second is the confirmed
start frame, the third is the confirmed end frame — plus the motion
description below, generate ONE new image: a storyboard grid of 8 panels
arranged in 2 columns x 4 rows, laid out in reading order (left-to-right,
top-to-bottom), representing a snapshot of the scene at each second from 0
through 7 of an 8-second continuous shot.

Panel order and timing:
- Row 1: 0s (top-left), 1s (top-right)
- Row 2: 2s, 3s
- Row 3: 4s, 5s
- Row 4: 6s, 7s

Each panel shows a small, clearly readable number label in one corner
("0s", "1s", ... "7s") so the sequence is easy to read at a glance.

Panel 0s must match the start reference image exactly. Panel 7s should be
close to the end reference image. In every panel, the character's face, fur
color/texture, and proportions must match the character reference image —
do not let appearance drift across panels. The panels in between should
show a plausible, smoothly progressing sequence of this motion:
- 0s: Chang-su faces the camera, holding the recycling load, door closed.
- 1s: he has turned around, back now facing the camera, leaning into the
  door and beginning to push it with his back.
- 2s: mid-struggle — leaning hard, legs pushing off the floor. The door has
  begun swinging open a little way under the pressure — a narrow gap of
  bright light shows at its edge. The door itself is completely undamaged
  and unmarked, simply opening on its hinge like normal; it must NOT show
  any cracks, fractures, or damage of any kind.
- 3s: the door has swung open further; he is stepping through the
  threshold. Still seen from BEHIND, face NOT visible. He is still
  carrying the exact same two items as before (the cardboard-and-cans
  bundle and the PET bottle bag) — they must still be visible in his wings.
- 4s: he is partway through the doorway, walking forward. Still seen from
  BEHIND, face NOT visible. Still carrying the same two items, clearly
  visible in his wings.
- 5s: Still seen from BEHIND — his face is NOT visible, his back is still
  fully to the camera (do not let him face camera again). He has now
  stepped all the way through the open doorway and is outside on the
  landing, continuing to walk with his path curving toward screen-RIGHT,
  positioned off-center toward the right side of the frame. Still carrying
  the same two items.
- 6s: Still seen from BEHIND, face NOT visible. He is almost completely
  exited — MORE THAN HALF of his body is already cropped off by the right
  edge of the frame, only a small portion (part of his back/head) still
  visible, still carrying what's visible of the two items. The door is
  STILL OPEN at this point — it has not started closing yet.
- 7s: he is completely gone from frame — no part of him visible anywhere.
  Only now does the door swing fully shut on its own, matching the end
  reference image exactly.

The 3s → 4s → 5s → 6s → 7s stretch is one single, continuous, natural exit
— not disconnected snapshots. Each panel must look like a direct, gradual
continuation of the one before it: his position, stride, and how much of
him is cropped by the frame edge should progress smoothly and believably.
Avoid any panel-to-panel jump that looks like a cut or a teleport, and
avoid any panel where he suddenly faces the camera again — once he turns
at 1s, his back stays to the camera for every remaining panel until he is
fully gone. Imagine this as flipping through consecutive frames of one
real walk out the door, not picking unrelated moments.

Camera position/framing, background, and character design must stay
consistent across all 8 panels — this is one continuous scene, not 8
separate images. Thin white borders/gutters between panels are fine so they
don't blend together.

No other text, logos, or watermarks besides the second-number labels.
```

> **그리드 v5는 물리적으로 모순된 구버전 로직을 담고 있음 — 소재(Ingredients) 모드 전환 전 v6로 재생성 필요**: v5 그리드의 1초 패널은 "이미 뒤돈 상태(등이 카메라 쪽)로 등으로 민다"로 만들어졌는데, 이는 이후 영상 프롬프트 작업 중(v9→v11) 발견한 물리적 모순(뒤돈 순간 정면이 문을 향하게 되어 등으로 미는 게 불가능)과 동일한 버그다. 그리드가 사람이 눈으로 확인하는 용도로만 쓰일 때는 문제가 드러나지 않았지만, **"소재" 모드에서는 그리드 이미지 자체가 영상 생성에 직접 참조 이미지로 들어가므로**, 텍스트 프롬프트가 "정면 유지"라고 명시해도 참조 이미지가 보여주는 구버전 자세(조기 회전)로 끌려갈 위험이 큼("참조 이미지가 텍스트 지시보다 강함" — 소품 좌우 반전 실패 사례 참고). 영상 프롬프트(v12)에서 이미 고친 로직(1s-2s 정면 유지, 3s에 딱 한 번 회전 + 랜드마크 체크포인트)에 맞춰 그리드도 다시 만들어야 함.

```
Using the three reference images — the first is Chang-su's character
reference (for exact face/eye/fur consistency), the second is the confirmed
start frame, the third is the confirmed end frame — plus the motion
description below, generate ONE new image: a storyboard grid of 8 panels
arranged in 2 columns x 4 rows, laid out in reading order (left-to-right,
top-to-bottom), representing a snapshot of the scene at each second from 0
through 7 of an 8-second continuous shot.

Panel order and timing:
- Row 1: 0s (top-left), 1s (top-right)
- Row 2: 2s, 3s
- Row 3: 4s, 5s
- Row 4: 6s, 7s

Each panel shows a small, clearly readable number label in one corner
("0s", "1s", ... "7s") so the sequence is easy to read at a glance.

Panel 0s must match the start reference image exactly. Panel 7s should be
close to the end reference image. In every panel, the character's face, fur
color/texture, and proportions must match the character reference image —
do not let appearance drift across panels. The panels in between should
show a plausible, smoothly progressing sequence of this motion:
- 0s: Chang-su faces the camera, holding the recycling load, door closed.
  His torso and face point straight at the camera.
- 1s (MOST IMPORTANT MOMENT): he is STILL fully facing the camera — no
  turning, no profile, no 3/4 angle. He has stepped backward so his back
  presses against the door, and is leaning his whole body weight back,
  pushing hard against the door with his back, straining, legs pushing
  against the floor for leverage. His face is still toward the camera
  (his head may tilt down slightly with visible effort, but his torso
  does not rotate). He must NOT be shown in profile or back-view here —
  showing him already turned around at this point is a failure state.
- 2s: he is STILL fully facing the camera, same orientation as 1s — no
  rotation yet. The push has finished and the door has swung open,
  already fully open by this panel. The door itself is completely
  undamaged and unmarked, simply opening on its hinge like normal; it
  must NOT show any cracks, fractures, or damage of any kind.
- 3s: NOW, for the first time, he has turned around so his back fully
  faces the camera, and his leading foot is already past the door's
  threshold line, stepping onto the outdoor landing. Face NOT visible
  from this point on. Still carrying the exact same two items, clearly
  visible in his wings.
- 4s: he is now clearly on the outdoor landing, roughly at the depth of
  the railing, walking forward. Still seen from BEHIND, face NOT visible,
  still carrying the same two items.
- 5s: Still seen from BEHIND — his face is NOT visible, his back is still
  fully to the camera (do not let him face camera again). He is
  continuing to walk with his path curving toward screen-RIGHT, now past
  the railing's midpoint, positioned off-center toward the right side of
  the frame. Still carrying the same two items.
- 6s: Still seen from BEHIND, face NOT visible. He is almost completely
  exited — MORE THAN HALF of his body is already cropped off by the right
  edge of the frame, only a small portion (part of his back/head) still
  visible, still carrying what's visible of the two items. The door is
  STILL OPEN at this point — it has not started closing yet.
- 7s: he is completely gone from frame — no part of him visible anywhere.
  Only now does the door swing fully shut on its own, matching the end
  reference image exactly.

The 3s → 4s → 5s → 6s → 7s stretch is one single, continuous, natural exit
— not disconnected snapshots. Each panel must look like a direct, gradual
continuation of the one before it: his position, stride, and how much of
him is cropped by the frame edge should progress smoothly and believably.
Avoid any panel-to-panel jump that looks like a cut or a teleport, and
avoid any panel where he suddenly faces the camera again — once he turns
at 3s, his back stays to the camera for every remaining panel until he is
fully gone. Likewise, avoid any panel before 3s where he appears turned or
in profile — before 3s he is always fully front-facing, only his posture
changes (standing, then leaning/straining into the push). Imagine this as
flipping through consecutive frames of one real sequence, not picking
unrelated moments.

Camera position/framing, background, and character design must stay
consistent across all 8 panels — this is one continuous scene, not 8
separate images. Thin white borders/gutters between panels are fine so they
don't blend together.

No other text, logos, or watermarks besides the second-number labels.
```

### v5 그리드 (참고용, 사용자 확인 완료했으나 이후 물리적 모순 발견되어 v6로 대체 필요)
> 0~4초 진행/2초 관용구/5초 뒷모습 유지/소품 유지/6초 타이밍 문제는 모두 해결되어 사용자가 확인한 버전이지만, **1초 패널의 "이미 뒤돈 채 등으로 밀기" 자체가 이후 발견된 물리적 모순을 담고 있음**. 소재 모드로 전환하며 v6로 대체.
```
(v5 그리드 프롬프트 전체 텍스트는 위 v6 항목 직전, 이 파일의 git 히스토리 참고)
```

## ③ 영상 연결 프롬프트 (Veo 3.1 Lite, v13 — "소재/Ingredients" 모드용)
> **모드 전환**: "시작/끝 프레임 → Frames to Video"에서 **"소재(Ingredients to Video)"** 방식으로 전환. 시작 프레임, 끝 프레임, 확정된 스토리보드 그리드(v6, 위 참고) 3장을 모두 참조 이미지로 첨부하고, 텍스트 프롬프트로 세 이미지의 역할과 초 단위 진행을 명시하는 구조.
> **Frames to Video와의 핵심 차이**: Frames to Video는 시작/끝 이미지 사이를 모델이 알아서 보간(interpolate)하지만, 소재 모드는 그런 보장이 없음 — 참조 이미지들은 스타일/구도/외형 참고 자료일 뿐, "영상이 반드시 이 이미지로 시작하고 이 이미지로 끝나야 한다"는 것도 텍스트로 명시해야 함. 대신 **스토리보드 그리드를 세 번째 소재로 직접 넣을 수 있다는 장점**이 있음 — 그리드가 이미 8개 패널로 초 단위 진행을 시각적으로 확정해놓았으므로, 텍스트만으로 매초 상태를 설명하던 것보다 훨씬 강력한 앵커가 될 수 있음(단, 그리드 자체가 정확해야 함 — 위 v6 재생성 이유 참고).
> **v11 영상 결과 분석(2fps)**: 몸 방향 논리(정면 유지하며 등으로 밀기 → 문 열린 후 1회 회전)는 물리적으로 문제없었고 실제로 그 순서를 어긴 렌더링 붕괴도 없었음. 하지만 **지시가 지켜지지 않고 타이밍이 드리프트하는 별개의 문제**가 발견됨:
> 1. **1s 시점에 이미 옆모습(프로필)으로 돌아가 있음** — "1s-2s 동안 정면 유지"라고 명시했는데도 회전이 훨씬 일찍(사실상 즉시) 시작되어, 정작 "등으로 문을 밀어서 여는" 씬의 핵심 장면이 정면이 아니라 옆모습으로 뭉개져서 나옴. 이게 사용자가 지적한 **문제 1("문을 등으로 바깥으로 밀어야 한다")**의 원인.
> 2. **3s에 회전은 정상적으로 일어났지만, 그 이후 3~4.5초 구간에서 캐릭터가 문턱 근처에 거의 정지된 채로 멈춰있음** — "매초 눈에 띄게 이동해야 한다"는 규칙이 있었는데도 지켜지지 않음. 그러다 5~6.5초에 뒤늦게 오른쪽으로 몰아서 이동. 실제로는 문을 통과해서 바깥 랜딩으로 나간 게 아니라 문턱 안쪽/문 앞에서 정지했다가 뒤늦게 옆으로 빠져나가는 것처럼 보임. 이게 사용자가 지적한 **문제 2("문을 열기만 하고 안쪽에서 오른쪽으로 걸어가고 있음")**의 원인.
> 3. v9에서 "무게감 있게(정성적)"가 "1s-2s(정량적)"를 압도했던 것과 같은 계열의 문제지만, 이번엔 그 반대 방향 구간(미는 구간이 아니라 통과하는 구간)에서 "매초 이동해야 한다"는 **추상적 규칙 자체가 충분히 구체적이지 않아서** 지켜지지 않은 것으로 판단.
>
> **v12 수정**: (1) 1s-2s 구간에 "옆모습/3쿼터 금지"라는 명시적 부정 제약을 추가해 회전이 새어나가는 것을 막음. (2) 3s 이후 구간의 "매초 이동" 규칙을 추상적 서술 대신 **도어매트 가장자리 / 문턱 라인 / 난간** 같은 화면에 실제로 보이는 구체적 랜드마크에 각 초의 위치를 고정하는 방식으로 교체 — "더 멀리 가야 한다"가 아니라 "이 초에는 반드시 이 랜드마크를 지나 있어야 한다"로 명시.
>
> **v10 시도 전, 사용자가 물리적 모순 지적**: 카메라를 보고 서있는 상태에서 문은 이미 캐릭터 뒤쪽에 있음(카메라→캐릭터→문 순서 배치). 그런데 v9/v10 프롬프트는 "뒤돌아서(등을 카메라 쪽으로) 등으로 문을 민다"고 했는데, 뒤돌면 정면이 문 쪽을 향하게 되므로 그 상태에서 "등으로" 미는 건 물리적으로 불가능함. 모델이 이 모순을 풀려다 문이 안쪽/바깥쪽으로 왔다갔다 하고 몸이 문에 섞여 들어가는 렌더링 붕괴를 일으킨 것으로 추정.
> **v11 수정**: **순서를 바꿈** — 뒤돌지 않은 상태(카메라를 보는 채로) 그대로 뒷걸음질로 문에 등을 대고 밀어서 연다(이 구간은 얼굴이 보임, 자연스러움). 문이 열린 다음에야 한 번 뒤돌아서 문 쪽으로 걸어나간다. "뒤돌기"를 미는 동작 이전이 아니라 **이후(3초 시점)**로 이동.
> **v9 영상 결과 분석(2fps)**: 최종 상태(문 닫힘, 빈 방)는 정확히 맞았고 문 디자인/외부 구조물 문제도 없었음(진전!). 다만 (1) 0~4초 동안 문 미는 동작에 시간이 너무 많이 쓰이고 캐릭터가 도어매트에서 거의 안 움직임, (2) 5.5~6초에 급하게 이동을 몰아 처리하려다 몸이 옆모습으로 홱 틀어지며 얼굴 일부가 노출되는 글리치 발생. **원인**: "MOST IMPORTANT MOMENT... 서두르지 말고 무게감 있게"라는 강조가 "1s-2s"라는 명시적 시간 제한보다 더 강하게 작용해서 문 미는 구간이 전체 러닝타임 절반을 잡아먹음 → 남은 "자연스럽게 걸어나가기" 구간이 급격히 압축되며 글리치 발생.
> **v10 수정(v11에도 유지)**: 문 미는 구간에 "무게감" 대신 **절대 시간 상한**을 못박고("2초를 넘기면 안 됨"), 이동 구간에 "매초 반드시 눈에 띄게 이동해야 한다"는 규칙 추가.
> **v8 → v9 변경 이유**: 확정된 스토리보드 그리드(나노바나나, 8컷)가 나왔으니, 동작을 처음부터 다시 구상하지 않고 **그리드의 초 단위 내용을 그대로 옮겨서** 작성. 그리드에서 검증된 교훈(관용구 금지, 매 비트마다 "뒷모습 유지"·"소품 유지" 반복 + 마지막에 요약 규칙, 긍정 서술+부정 제약 페어)도 영상 프롬프트에 동일하게 적용.
> **v7 → v8 변경 이유(사용자 지적)**: "등으로 문을 힘겹게 밀어서 여는 것"이 이 씬의 핵심 포인트인데, CRITICAL RULES 등 다른 세부 규칙들 사이에 묻혀서 강조가 부족했음 → 이 동작을 프롬프트 최상단에 **가장 중요한 순간(MOST IMPORTANT MOMENT)**으로 분리해서 구체적인 신체 동작(온 몸을 뒤로 기대어 밀기, 다리로 바닥을 밀어내기, 문이 살짝 버티다가 밀려 열림 등)으로 생생하게 묘사.
> **v6 → v7 변경 이유(사용자 지적)**: 문이 바깥쪽으로 열려야 하는데 그렇지 않았고, 문 열렸을 때 바깥 풍경 안에 "문처럼 생긴 구조물"이 또 보여서 어색함 → 문이 확실히 바깥 방향으로 열리고, 문 밖은 순수한 야외 배경(하늘/바닥/난간/나무 등)만 보이도록 명시.
> **컨셉**: 정면으로 서있다가 → 뒤돌아 **등으로 문을 힘겹게 밀어서 열고** → 문밖으로 나가서 **오른쪽 방향으로 이동**하며 화면에서 점점 멀어짐 → **도어클로저(자동 닫힘 장치)로 문이 저절로 닫힘** → 마지막엔 캐릭터 없는 빈 현관+문 닫힘(끝 프레임 v16과 매칭). 카메라 완전 고정, 대사/텍스트 없음, 잔잔한 배경음악 + 효과음만.
> **v4 → v5 변경 이유**: 사용자 요청으로 퇴장 방향을 **오른쪽**으로 명시.
>
> **v5 영상 결과 분석(2fps 프레임 분석) — 심각한 렌더링 붕괴 발견**:
> - 0.5초: 눈이 흰자만 보이게 이상해짐, 문손잡이 소실
> - 1.5~2.0초: 페트병 봉지가 몸에서 떨어져 바닥에 방치된 것처럼 렌더링됨
> - 2.0초: 종이박스 묶음 완전히 사라짐
> - 2.0~4.0초: **문 디자인 자체가 갈색 나무문 → 흰색 유리패널 문 → 갈색 문으로 계속 바뀜**
> - 4.5~5.5초: **가장 심각** — 캐릭터가 갑자기 다시 정면을 보며 문 뒤에서 겁먹은 표정으로 쳐다봄, 몸 색깔이 파란빛으로 변함, 몸이 문짝에 반투명하게 섞여 들어가는 렌더링 붕괴(고스팅)
> - 6.0초: 문이 이미 완전히 닫혔는데 캐릭터는 여전히 화면 안(집 안)에 서있음 — "나간 뒤 문이 닫힌다"는 논리 자체가 깨짐
> - 7.0~7.5초: 최종적으로는 목표(빈 방, 문 닫힘)에 도달
>
> **원인 재분석(사용자 지적으로 재검토)**: 단계 수 문제가 아니라 프롬프트 문구 자체의 구체적 결함 3가지로 재진단함.
> 1. **"turns and heads toward screen-RIGHT"의 "turns"가 "몸을 돌려라(카메라 쪽으로 재회전)"로 오독된 것으로 추정** — 실제로 캐릭터가 다시 정면을 보인 구간(4.5~5.5초)과 일치. "몸 방향(뒷모습)은 그대로 두고 걷는 경로만 오른쪽으로 휜다"는 걸 "turn"이라는 단어 없이 명확히 구분해서 표현해야 함.
> 2. **"문이 열린 상태"를 보여주는 참조 이미지가 전혀 없음** — 시작/끝 프레임이 둘 다 문 닫힘이라, 중간에 문이 열린 모습은 순수하게 텍스트로만 상상해서 그려야 했음 → 매번 다른 문 디자인(나무문/유리문)으로 그려진 원인. 문이 열려있을 때도 "참조 이미지와 같은 문"이라고 명시적으로 앵커링 필요.
> 3. **"문이 닫히는 타이밍"이 "캐릭터 퇴장"과 연동되어 있지 않음** — "끝나갈 때 저절로 닫힌다"고만 해서, 모델이 캐릭터 이동은 못 맞추면서 문 닫힘 타이밍만 시간 기준으로 지켜버림(캐릭터가 아직 안에 있는데 문이 닫힘). "캐릭터가 완전히 퇴장한 다음에만" 닫히라고 조건부로 명시 필요.

```
Using the three uploaded reference images as the basis for this video:
- The FIRST image is the exact opening moment of this video. The video
  must begin matching it essentially exactly — same character pose, same
  items in his wings, same closed door, same camera framing.
- The SECOND image is the exact final moment of this video. The video must
  end matching it essentially exactly — the same empty entryway with the
  door fully closed, no character visible anywhere.
- The THIRD image is an 8-panel storyboard grid (2 columns x 4 rows, read
  left-to-right top-to-bottom, labeled 0s through 7s) that shows exactly
  what happens in every second between the first and second image. Treat
  this grid as the authoritative second-by-second script for this video —
  every panel's pose, camera framing, door state, and character position
  must be reproduced at its labeled second, staged as smooth, continuous,
  natural 24fps motion rather than jumping between 8 discrete snapshots.
  Do not invent a different motion than what the grid shows.

Generate an 8-second continuous video, camera completely static — no
panning, no zooming, no cuts — fixed in the entryway of an ordinary home,
facing the front door, matching the framing of all three reference images.
Visible landmarks in this fixed shot: the doormat directly in front of the
door, the door's own threshold line, and (once the door is open) a railing
out on the landing beyond it. Use these landmarks as fixed position
checkpoints — they do not move, only Chang-su moves relative to them.

Follow the storyboard grid (third image) second by second:
- 0s: Chang-su faces the camera, holding a heavy load of recycling (a tied
  cardboard bundle with a mesh bag of cans hooked to it in one
  wing-flipper, a clear bag of PET bottles in the other). Door closed,
  directly behind him. His torso and face are pointed straight at the
  camera.
- 1s (MOST IMPORTANT MOMENT — brief but forceful, NOT slow): his torso and
  face are STILL pointed straight at the camera, exactly as at 0s — no
  rotation, no turning, not even a partial turn. He takes a step backward
  so his back presses against the door, then leans his whole body weight
  back and pushes hard against the door with his back, straining, legs
  pushing against the floor for leverage. He must NOT be shown in
  profile, 3/4 view, or any angle other than fully front-facing at this
  moment — if his body appears to be turning or angled to the side at 1s,
  that is a failure state.
- 2s: he is STILL fully front-facing the camera, same as 1s — still no
  rotation. The push finishes and the door swings open outward, away from
  him and away from the camera — by the END of this second the door must
  already be fully open. The door itself is completely undamaged and
  unmarked, simply opening on its hinge like normal — it must NOT show any
  cracks, fractures, or damage of any kind. THE DOOR-PUSH BEAT IS NOW
  OVER — it must not continue into 3s.
- 3s: NOW, for the first (and only) time, he turns his body around so his
  back fully faces the camera, and immediately steps forward through the
  open doorway. By the END of this second, his leading foot must already
  be past the door's threshold line — physically standing on the outdoor
  landing surface, not merely turned around while still standing on the
  doormat. Face NOT visible from this point on. Still carrying the exact
  same two items, clearly visible in his wings.
- 3.5s: both feet are now on the outdoor landing surface, clearly past the
  threshold line, with the doorway frame visibly behind him. He is not
  lingering at the threshold — standing at or just inside the threshold
  at this point is a failure state, even if his body has already turned.
- 4s: he has taken several more steps onto the landing and is now roughly
  at the same depth as the railing, clearly and unmistakably farther from
  the door than at 3.5s. Still seen from BEHIND, face NOT visible, still
  carrying the same two items.
- 4.5s-5s: continuing to walk on the landing, now visibly curving his path
  toward screen-RIGHT, moving past the midpoint of the railing toward its
  right end. Clearly farther right than at 4s. Still seen from BEHIND,
  back fully to camera — do NOT let him turn or show his face here.
- 5.5s-6s: he is near the right end of the railing, almost completely
  exited — MORE THAN HALF of his body is already cropped off by the right
  edge of the frame, only a small portion still visible. The door is
  STILL OPEN at this point — it has not started closing yet. Still seen
  from BEHIND, face NOT visible — he must not spin or jerk toward camera
  to cover distance quickly.
- 6.5s-7s: he is completely gone from frame — no part of him visible
  anywhere. Only now does the door's self-closing hinge mechanism swing it
  fully shut on its own, arriving closed by the very end of the clip.

The 3s → 3.5s → 4s → 4.5s → 5s → 5.5s → 6s stretch is one single,
continuous, natural exit, not disconnected moments — his position relative
to the threshold line and the railing should progress smoothly and
believably, like consecutive frames of one real walk out the door and
across the landing. Each checkpoint above (past the threshold by 3.5s, at
the railing's depth by 4s, past the railing's midpoint by 4.5s-5s, more
than half-cropped by 5.5s-6s) is a hard requirement, not a suggestion —
reaching a checkpoint late, or standing near the threshold/doormat for
more than one of these listed moments, is a failure state exactly as much
as a physically impossible pose would be.

The door itself — the same solid brown wooden door with the same silver
lever handle and door-closer arm hardware seen in the reference images —
stays visually consistent throughout, whether closed, opening, or open. It
does not change color, material, or hardware design at any point. Because
he backs into it and pushes with his back while still facing camera, the
door swings outward, away from him and away from the camera, out into the
exterior space — it must NEVER swing inward toward the camera/character,
and must never appear to open toward him or trap/press against him.

Beyond the doorway, only ordinary outdoor scenery is visible: sky, the
outdoor landing/walkway floor, a railing, trees or greenery, maybe a
neighboring building in the distance. There must be NO other door, gate,
screen door, or any door-like structure of any kind visible in the
exterior — just a normal outdoor space.

CRITICAL RULES (do not violate these):
- The video's opening frame must match the FIRST reference image
  essentially exactly, and the video's closing frame must match the
  SECOND reference image essentially exactly. Do not drift away from
  either reference image's pose, framing, or state.
- The storyboard grid (third reference image) is the authoritative source
  for what happens at each second — do not invent a different motion,
  pose, or staging than what it shows, even if it would otherwise seem
  reasonable. Where this text and the grid appear to conflict, the grid's
  visual staging for orientation/pose takes precedence, but the explicit
  timing/checkpoint rules below (which refine the grid with lessons from
  prior failed attempts) must still be followed.
- Chang-su does NOT turn around to push the door. He pushes it open with
  his back while still facing generally toward the camera (backing into
  it) — turning around first and then pushing with his back is physically
  impossible (his front, not his back, would face the door) and must not
  happen.
- Before 3s, Chang-su is ALWAYS fully front-facing the camera — never in
  profile, never at a 3/4 angle, never mid-turn. There are only two valid
  orientations in this entire clip: fully front-facing (0s-2s) and fully
  back-facing (3s onward, after the single turn). Any angle in between,
  at any point, is a failure state — this applies most strictly at 1s-2s,
  where the temptation is to start rotating early to look more natural;
  resist that, the rotation must be held until exactly 3s.
- The door-push struggle happens ONLY within 1s-2s and must be finished —
  door fully open — by the end of 2s. It must NOT extend into 3s or
  beyond. Make it visually strong and clear within that short window
  rather than stretching it out slowly.
- Chang-su turns his body only ONCE, at 3s (after the door is already
  open), to face away from camera. After that single turn, he must NEVER
  face the camera again and must NEVER rotate his body for the rest of
  the clip, all the way through 7s — only his walking path curves toward
  screen-RIGHT, his back stays to the camera throughout every remaining
  second. This applies just as strictly at 5s-6s as it does right after
  the turn — do not let him spin toward camera to cover ground quickly.
- Chang-su must be standing on the outdoor landing surface, past the
  door's threshold line, no later than 3.5s. Being turned around but still
  standing on the doormat or at the threshold past 3.5s is a failure
  state — the turn and the actual step through the doorway happen
  together, not turn-then-pause-then-step.
- From 3s through 6s, Chang-su must hit each landmark-based checkpoint
  above (threshold by 3.5s, railing depth by 4s, past railing midpoint by
  4.5s-5s, more than half-cropped by 5.5s-6s) on schedule. He must never
  remain within one landmark's distance of his previous position for more
  than the one checkpoint it belongs to, and he must never skip a
  checkpoint by jumping straight to a later one.
- The door's appearance (color, material, handle, closer hardware) stays
  perfectly consistent throughout — always the same door as in the
  reference images, never a different design, and never showing cracks or
  damage.
- The door swings outward (away from camera, into the exterior), never
  inward toward the camera.
- The exterior beyond the doorway is plain outdoor scenery only — no
  additional doors or door-like structures anywhere in the background.
- The door does not start closing until Chang-su has completely exited the
  frame (see 6s vs 7s above) — character-exit happens first, door-closing
  happens second, these must not overlap.
- Chang-su moves continuously away from camera for the entire clip once he
  starts walking (3s onward). He must never stand still, walk in place, or
  move backward toward camera.
- The two items he carries stay solid and continuously visible while he is
  on screen. They must not flicker, disappear, or change shape.
- Do not repeat, loop, hesitate, or reverse any part of the motion.

His body leans/wobbles slightly side to side as he walks, working to keep
his balance under the load — a natural, subtle wobble, not exaggerated.
He never drops or spills anything.

Motion should be natural and continuous, not exaggerated or cartoonish.

Audio: gentle, soft background music throughout (calm, warm, understated
mood). Light, realistic sound effects only — a soft effort/grunt sound as
he pushes the door with his back, a door creak as it opens, footsteps
fading as he walks away, and a soft door-closer click/thud as the door
swings shut on its own near the end. NO dialogue, NO voiceover, NO
on-screen text or captions.
```

### v12 (참고용, Frames to Video 모드용 — 아직 테스트 전, 소재 모드로 전환하며 v13으로 대체)
> v11의 2fps 분석 결과(방향 드리프트 + 문턱 정지)를 고쳐서 작성했으나, 사용자가 생성 방식을 "시작/끝 프레임(Frames to Video)"에서 "소재(Ingredients to Video)"로 바꾸기로 하면서 실제 테스트 없이 v13으로 대체됨. 랜드마크 체크포인트/프로필 금지 로직 자체는 v13에 그대로 이어짐 — 차이는 참조 이미지(그리드 포함) 활용 방식과 프롬프트 서두 구조뿐.
```
An 8-second continuous shot, camera completely static — no panning, no
zooming, no cuts — fixed in the entryway of an ordinary home, facing the
front door. Visible landmarks in this fixed shot: the doormat directly in
front of the door, the door's own threshold line, and (once the door is
open) a railing out on the landing beyond it. Use these landmarks as fixed
position checkpoints — they do not move, only Chang-su moves relative to
them.

- 0s: Chang-su faces the camera, holding a heavy load of recycling (a tied
  cardboard bundle with a mesh bag of cans hooked to it in one
  wing-flipper, a clear bag of PET bottles in the other). Door closed,
  directly behind him. His torso and face are pointed straight at the
  camera.
- 1s (MOST IMPORTANT MOMENT — brief but forceful, NOT slow): his torso and
  face are STILL pointed straight at the camera, exactly as at 0s — no
  rotation, no turning, not even a partial turn. He takes a step backward
  so his back presses against the door, then leans his whole body weight
  back and pushes hard against the door with his back, straining, legs
  pushing against the floor for leverage. He must NOT be shown in
  profile, 3/4 view, or any angle other than fully front-facing at this
  moment — if his body appears to be turning or angled to the side at 1s,
  that is a failure state.
- 2s: he is STILL fully front-facing the camera, same as 1s — still no
  rotation. The push finishes and the door swings open outward, away from
  him and away from the camera — by the END of this second the door must
  already be fully open. The door itself is completely undamaged and
  unmarked, simply opening on its hinge like normal — it must NOT show any
  cracks, fractures, or damage of any kind. THE DOOR-PUSH BEAT IS NOW
  OVER — it must not continue into 3s.
- 3s: NOW, for the first (and only) time, he turns his body around so his
  back fully faces the camera, and immediately steps forward through the
  open doorway. By the END of this second, his leading foot must already
  be past the door's threshold line — physically standing on the outdoor
  landing surface, not merely turned around while still standing on the
  doormat. Face NOT visible from this point on. Still carrying the exact
  same two items, clearly visible in his wings.
- 3.5s: both feet are now on the outdoor landing surface, clearly past the
  threshold line, with the doorway frame visibly behind him. He is not
  lingering at the threshold — standing at or just inside the threshold
  at this point is a failure state, even if his body has already turned.
- 4s: he has taken several more steps onto the landing and is now roughly
  at the same depth as the railing, clearly and unmistakably farther from
  the door than at 3.5s. Still seen from BEHIND, face NOT visible, still
  carrying the same two items.
- 4.5s-5s: continuing to walk on the landing, now visibly curving his path
  toward screen-RIGHT, moving past the midpoint of the railing toward its
  right end. Clearly farther right than at 4s. Still seen from BEHIND,
  back fully to camera — do NOT let him turn or show his face here.
- 5.5s-6s: he is near the right end of the railing, almost completely
  exited — MORE THAN HALF of his body is already cropped off by the right
  edge of the frame, only a small portion still visible. The door is
  STILL OPEN at this point — it has not started closing yet. Still seen
  from BEHIND, face NOT visible — he must not spin or jerk toward camera
  to cover distance quickly.
- 6.5s-7s: he is completely gone from frame — no part of him visible
  anywhere. Only now does the door's self-closing hinge mechanism swing it
  fully shut on its own, arriving closed by the very end of the clip.

(나머지 CRITICAL RULES/오디오 등은 v13과 랜드마크 체크포인트 부분 제외 동일 — 전체 텍스트는 git 히스토리 참고)
```

### v11 (참고용, 2fps 분석 결과 실패) — 방향 논리는 맞았으나 타이밍 드리프트(프로필 조기 회전 + 문턱에서 정지)
> 실패 원인 상세는 위 v12 항목의 "v11 영상 결과 분석" 참고.
```
An 8-second continuous shot, camera completely static — no panning, no
zooming, no cuts — fixed in the entryway of an ordinary home, facing the
front door. This is the exact motion depicted in the confirmed 8-panel
storyboard grid (0s-7s) — follow it second by second:

- 0s: Chang-su faces the camera, holding a heavy load of recycling (a tied
  cardboard bundle with a mesh bag of cans hooked to it in one
  wing-flipper, a clear bag of PET bottles in the other). Door closed,
  directly behind him.
- 1s (MOST IMPORTANT MOMENT — brief but forceful, NOT slow): still facing
  generally toward the camera (do NOT turn around yet), he takes a step
  backward so his back presses against the door, then leans his whole body
  weight back and pushes hard against the door with his back, straining,
  legs pushing against the floor for leverage. His face/front is still
  visible toward camera during this push — he has not turned around.
- 2s: the push finishes and the door swings open outward, away from him
  and away from the camera — by the END of this second the door must
  already be fully open. The door itself is completely undamaged and
  unmarked, simply opening on its hinge like normal — it must NOT show any
  cracks, fractures, or damage of any kind. THE DOOR-PUSH BEAT IS NOW
  OVER — it must not continue into 3s. He still has not turned around yet.
- 3s: NOW, for the first (and only) time, he turns around so his back
  fully faces the camera, and immediately begins stepping through the open
  threshold, walking briskly. Face NOT visible from this point on. Still
  carrying the exact same two items, clearly visible in his wings.
- 4s: he is now clearly past the doorway, well out onto the landing,
  walking forward at a steady pace. Still seen from BEHIND, face NOT
  visible, still carrying the same two items. He must look noticeably
  farther along than at 3s.
- 5s: Still seen from BEHIND, back fully to camera — do NOT let him turn
  or show his face here. He is continuing to walk with his path curving
  toward screen-RIGHT, now positioned off-center toward the right side of
  the frame, clearly farther right than at 4s. Still carrying the same two
  items.
- 6s: Still seen from BEHIND, face NOT visible — he must not spin or jerk
  toward camera to cover distance quickly. He is almost completely exited
  — MORE THAN HALF of his body is already cropped off by the right edge of
  the frame, only a small portion still visible. The door is STILL OPEN at
  this point — it has not started closing yet.
- 7s: he is completely gone from frame — no part of him visible anywhere.
  Only now does the door's self-closing hinge mechanism swing it fully
  shut on its own, arriving closed by the very end of the clip.

The 3s → 4s → 5s → 6s → 7s stretch is one single, continuous, natural
exit, not disconnected moments — his position, stride, and how much of
him is cropped by the frame edge should progress smoothly and believably,
like consecutive frames of one real walk out the door. He must show
visible, real forward progress in EVERY one of these seconds — he must
never hold nearly the same position for more than one second, and he must
never cover a large distance in one sudden jump between two seconds.

The door itself — the same solid brown wooden door with the same silver
lever handle and door-closer arm hardware seen in the reference images —
stays visually consistent throughout, whether closed, opening, or open. It
does not change color, material, or hardware design at any point. Because
he backs into it and pushes with his back while still facing camera, the
door swings outward, away from him and away from the camera, out into the
exterior space — it must NEVER swing inward toward the camera/character,
and must never appear to open toward him or trap/press against him.

Beyond the doorway, only ordinary outdoor scenery is visible: sky, the
outdoor landing/walkway floor, a railing, trees or greenery, maybe a
neighboring building in the distance. There must be NO other door, gate,
screen door, or any door-like structure of any kind visible in the
exterior — just a normal outdoor space.

CRITICAL RULES (do not violate these):
- Chang-su does NOT turn around to push the door. He pushes it open with
  his back while still facing generally toward the camera (backing into
  it) — turning around first and then pushing with his back is physically
  impossible (his front, not his back, would face the door) and must not
  happen.
- The door-push struggle happens ONLY within 1s-2s and must be finished —
  door fully open — by the end of 2s. It must NOT extend into 3s or
  beyond. Make it visually strong and clear within that short window
  rather than stretching it out slowly.
- Chang-su turns his body only ONCE, at 3s (after the door is already
  open), to face away from camera. Before 3s he faces generally toward
  the camera (needed to push the door with his back); after that single
  turn at 3s, he must NEVER face the camera again and must NEVER rotate
  his body for the rest of the clip, all the way through 7s — only his
  walking path curves toward screen-RIGHT, his back stays to the camera
  throughout every remaining second. This applies just as strictly at
  5s-6s as it does right after the turn — do not let him spin toward
  camera to cover ground quickly.
- From 3s through 6s, Chang-su must show clear, visible forward progress
  in EVERY single second. He must never remain in nearly the same
  position for more than one consecutive second, and he must never cover
  a large distance in one abrupt jump — the walk must look gradual and
  continuous across these seconds, not front-loaded pushing followed by a
  rushed catch-up.
- The door's appearance (color, material, handle, closer hardware) stays
  perfectly consistent throughout — always the same door as in the
  reference images, never a different design, and never showing cracks or
  damage.
- The door swings outward (away from camera, into the exterior), never
  inward toward the camera.
- The exterior beyond the doorway is plain outdoor scenery only — no
  additional doors or door-like structures anywhere in the background.
- The door does not start closing until Chang-su has completely exited the
  frame (see 6s vs 7s above) — character-exit happens first, door-closing
  happens second, these must not overlap.
- Chang-su moves continuously away from camera for the entire clip once he
  starts walking (3s onward). He must never stand still, walk in place, or
  move backward toward camera.
- The two items he carries stay solid and continuously visible while he is
  on screen. They must not flicker, disappear, or change shape.
- Do not repeat, loop, hesitate, or reverse any part of the motion.

His body leans/wobbles slightly side to side as he walks, working to keep
his balance under the load — a natural, subtle wobble, not exaggerated.
He never drops or spills anything.

Motion should be natural and continuous, not exaggerated or cartoonish.

Audio: gentle, soft background music throughout (calm, warm, understated
mood). Light, realistic sound effects only — a soft effort/grunt sound as
he pushes the door with his back, a door creak as it opens, footsteps
fading as he walks away, and a soft door-closer click/thud as the door
swings shut on its own near the end. NO dialogue, NO voiceover, NO
on-screen text or captions.
```

### v10 (참고용, 시도 전 폐기) — 물리적으로 모순된 지시("뒤돈 채 등으로 밀기")를 그대로 가지고 있었음
- v9의 타이밍 문제만 고치고 "뒤돌아서 등으로 민다"는 근본 모순은 그대로였음. 사용자가 지적해서 시도해보지 못하고 v11로 대체.

### v9 (참고용) — 스토리보드 그리드 기반, 최종 상태는 정확했으나 타이밍 배분 실패
- 결과: 문 디자인/외부 구조물 문제는 해결됨(진전). 문 미는 동작이 "MOST IMPORTANT MOMENT... 서두르지 말고"라는 강조 때문에 0~4초까지 늘어져서 캐릭터가 거의 안 움직임 → 5.5~6초에 이동을 몰아 처리하며 옆모습 글리치.
- 교훈: "무게감 있게, 서두르지 말라"는 정성적 강조가 "1s-2s"라는 정량적 시간 제한을 압도할 수 있음. 특정 비트에 시간을 많이 쓰길 원치 않으면 "unhurried/weighty" 같은 표현 대신 **명시적 상한("must be finished by Xs")**을 쓰고, 나머지 구간엔 "매초 진행이 있어야 한다"는 규칙을 강제할 것.

### v8 (참고용, 스토리보드 그리드 확정 전 독자적으로 구상한 버전)
- v7의 "MOST IMPORTANT MOMENT" 구조는 잘 작동해서 v9에서도 유지. 다만 동작을 처음부터 다시 구상했었는데, 이후 스토리보드 그리드로 검증된 초 단위 내용이 나와서 v9는 그걸 그대로 옮겨씀. 아직 실제 영상으로 테스트되지 않음.

### v5 (참고용, 렌더링 붕괴로 재작성) — 문 디자인 변경/캐릭터 재정면화/문-퇴장 논리 붕괴
- 결과는 위 v6 항목 상단의 "v5 영상 결과 분석" 참고. 원인 3가지(turn 단어 오독, 열린 문 레퍼런스 부재, 퇴장-닫힘 타이밍 미연동)를 찾아 v6로 수정.

### v4 (참고용, 퇴장 방향 미지정 — 실제 테스트 전에 방향 추가 요청으로 v5 작성)

### v3 (참고용, 끝 프레임 컨셉이 바뀌어서 폐기 — 실제 테스트도 안 됨)
```
An 8-second continuous shot, camera completely static — no panning, no
zooming, no cuts — fixed in the entryway of an ordinary home, looking
toward the open front door and the outdoor landing beyond it.

Chang-su, a small fluffy 3D-pixar-style penguin character, starts facing
the camera, holding a heavy load of recycling: a tied cardboard bundle
with a mesh bag of cans hooked to it in one wing-flipper, a clear bag of
PET bottles in the other. The front door in front of him is closed.

In one single continuous motion, with no pauses, no reversals, and no
repeated actions: he turns around away from the camera, pushing the door
open with his body as he turns, and immediately begins walking steadily
toward the open doorway and beyond it. He keeps moving forward for the
entire remainder of the clip — through the doorway, out onto the outdoor
landing, and continuing several more steps toward the railing — getting
smaller in the frame with every second as he gets farther from the fixed
camera, ending up noticeably small and distant by the final frame,
matching a wide shot of him standing near the railing with buildings and
sky visible around him.

CRITICAL RULES (do not violate these):
- The door opens exactly once, early in the clip, and then stays open for
  the rest of the video. It must never close again, even partially, at
  any point after it opens.
- Chang-su moves continuously forward/away from camera for the entire
  clip, covering a large distance — from standing just inside the door to
  standing far out near the railing. He must never stand still, walk in
  place, or move backward — there must be clear, steady progress in every
  second of footage, from start to finish. The amount of walking should
  feel proportional to the distance covered, not a small shuffle.
- The two items he carries stay solid and continuously visible the entire
  time. They must not flicker, disappear, or change shape.
- Do not repeat, loop, hesitate, or reverse any part of the motion.

His body leans/wobbles slightly side to side as he walks, working to keep
his balance under the load — a natural, subtle wobble, not exaggerated.
He never drops or spills anything.

Motion should be natural and continuous, not exaggerated or cartoonish.

Audio: gentle, soft background music throughout (calm, warm, understated
mood). Light, realistic sound effects only — a door creak/click as it
opens, soft footsteps (getting fainter as he gets farther away), a faint
rustle of the plastic bag and clinking cans. NO dialogue, NO voiceover,
NO on-screen text or captions.
```

### v2 (참고용, 실제 테스트 전에 끝 프레임이 바뀌어서 폐기)
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
