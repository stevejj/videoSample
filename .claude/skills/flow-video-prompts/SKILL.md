---
name: flow-video-prompts
description: Write and validate Google Flow prompts (Nano Banana start/end frame images + Veo 3.1 Lite video-connect prompt) for the 팽창수/팽미순 penguin-couple short-form video series in this repo. Use this whenever the user wants to plan a new 8-second scene, write image or video prompts for Flow, debug why a Nano Banana or Veo generation came out wrong, or asks to continue the "다음 씬" / "scene N" workflow — even if they don't say "skill" or reference this file directly. Also use it when the user shares a generated image or .mp4 from Flow and asks whether it looks right.
---

# Flow Video Prompts (팽창수/팽미순 series)

This skill packages the workflow this project converged on after ~20 rounds of
trial and error in the first scene. **The accumulated ground truth lives in two
files — read them before writing anything:**

- `README.md` — character sheet, workflow steps, and the "제작 가이드라인" /
  "프롬프트 검증 체크리스트" sections. This is the living rulebook; it has been
  updated after every failure mode discovered so far. Read it in full each time
  this skill triggers, since it changes as new lessons are learned.
- `scenes/scene-01.md` — a worked example showing the full version history
  (v1→v16 for frames, v1→v8 for video) with what failed and why. Skim it for
  concrete before/after prompt wording when you hit a failure mode that looks
  similar to one already solved there.

Treat README.md as the source of truth. If something in this SKILL.md
contradicts it, README.md wins — update this file to match rather than the
other way around.

## The end-to-end flow for a new scene

1. **Brainstorm the concept with the user** before writing any prompt. Nail
   down: who appears, tone/genre, setting, the single clear action, and how it
   ends. Don't skip to prompt-writing on a vague premise — every wasted
   iteration in scene-01 traced back to an underspecified concept.
2. **Check the camera/character/destination geometry** before describing any
   movement. If a destination (a door, an exit) is behind the character in
   frame, walking toward it means moving away from camera and turning around
   — not staying front-facing while advancing. Sketch this out mentally before
   writing the end-frame prompt; getting it wrong costs several rounds later.
   This applies to the video-connect prompt too, one level more specific:
   trace which direction each body part actually faces at each moment.
   "Facing the camera" already means the back faces away from camera, toward
   whatever is behind the character. Writing "he turns around, then pushes
   the door with his back" after that point is a physical contradiction —
   once turned, his front faces the door, not his back. An action requiring
   a specific body part to contact a specific surface (like backing into a
   door because the hands are full) has to be placed at the moment that part
   is actually oriented toward that surface — here, that means doing it
   *before* the turn, while still facing camera, and moving the turn to
   after the door is already open. Getting this backward produced visible
   breakdown in the actual Veo output (the door direction flickering, the
   character's body seeming to merge into the door) rather than just a
   logical oddity — the model tries to reconcile the contradiction and fails
   visibly.
3. **Write the start-frame prompt** (Nano Banana). Attach the relevant
   character reference image(s) only — one character reference if solo, two if
   both appear together (see README's "캐릭터 인식 원리" section for how to
   disambiguate two characters without relying on their names).
4. **Write the end-frame prompt.** Attach the character reference + the
   confirmed start frame as a second reference, and edit forward from it. Put
   required changes in a clear, loud block at the top of the prompt — the
   single most reliable failure mode is a change getting lost among "keep the
   same" language, so isolate what must change from what must stay identical.
5. **Verify both frames against the checklist in README.md** before handing
   them to the user, and again after they generate them and share the result.
6. **Before generating anything that describes motion (a storyboard grid or
   a video-connect prompt), self-check it for body-orientation feasibility
   and show that check to the user — this costs zero Flow credits, it's pure
   reading.** Write out a short per-timestamp table: what direction the
   character's front/back faces, and whether the described action at that
   moment is physically possible given that orientation (see the scene-01
   door-push contradiction in step 2 above for the exact kind of bug this
   catches). Do this BEFORE spending the user's time on a grid generation,
   not just before the video prompt — a flawed motion plan produces a
   flawed grid too, so catching it earlier saves a full round-trip. Only
   after this check comes back clean should the grid or video prompt
   actually be written/sent.
7. **Once both frames are confirmed (and the orientation check above is
   clean), ask the user whether to generate a storyboard-grid check before
   writing the video prompt.** Don't just do this automatically — always
   ask first. The point is that Nano Banana (images) costs no Flow credits
   but Veo (video) does, so a free intermediate sanity check catches a bad
   motion plan before it burns a paid generation. If they say yes, write a
   storyboard-grid prompt (see "Storyboard grid" below) attaching both
   confirmed frames as references, have them generate it, and review it
   together. Iterate on the grid (not the actual video prompt yet) until
   the per-second progression looks right — same iteration mindset as the
   frames themselves.
8. **Write the video-connect prompt (Veo 3.1 Lite) from the confirmed
   storyboard grid**, not from scratch. Once the grid looks right, the beats
   in the motion prompt should describe what's actually in each panel — the
   grid is now the validated spec for what happens second by second, so lean
   on it rather than re-inventing the motion description independently. (If
   the user skipped the grid step, fall back to drafting the motion directly
   from the concept as before.) Keep the motion to at most 2-3 clearly staged
   beats; if there's a single emotional/comedic core action, give it its own
   loud paragraph (e.g. "MOST IMPORTANT MOMENT") rather than letting it blend
   into a list of rules. State hard constraints as CRITICAL RULES, phrased as
   conditions ("X only happens after Y is 100% true"), not as time cues
   ("near the end").
9. **After the user shares the generated .mp4, extract frames at ~2fps and
   inspect every one before judging the result** — don't just skim the first
   and last frame. See "Verifying a generated video" below for the exact
   commands. Report findings with timestamps, then decide whether the
   fix is a wording problem in the prompt or a scope problem in the request.

## Storyboard grid (free pre-check before spending Veo credits)

Once start/end frames are confirmed and the user opts in, write a Nano Banana
prompt like this (fill in the bracketed parts from the scene's planned
motion beats):

```
Using the three reference images — the first is [character]'s character
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
[short bullet list of the planned story beats, same beats you'd otherwise
put straight into the video prompt]

Camera position/framing, background, and character design must stay
consistent across all 8 panels — this is one continuous scene, not 8
separate images. Thin white borders/gutters between panels are fine so they
don't blend together.

No other text, logos, or watermarks besides the second-number labels.
```

**Attach 3 references, in this order: (1) the character reference image,
(2) the confirmed start frame, (3) the confirmed end frame.** The middle
panels depict novel poses that appear in neither bookend frame (mid-push,
mid-stride), so the character reference matters here the same way it does
for end-frame prompts — without it, appearance can drift across panels. If
the end frame hasn't actually been generated and confirmed as a standalone
image yet (don't assume a video result's last frame counts — check the
scene file's status checklist), get that done first.

If the grid reveals a problem (motion that doesn't fit the timing, an
implausible jump between panels, a pose that doesn't make sense), fix it by
regenerating the grid — this is the cheap place to catch it. Once the user
is happy with
the grid, move to writing the actual video-connect prompt (step 7 above),
transcribing each panel's state into the corresponding beat of the motion
description.

**Failure patterns specific to multi-panel grids** (found and confirmed fixed
on scene 1's grid — check for these any time a grid has more than 2-3 panels):

- **A constraint stated once at the top doesn't reliably carry across many
  panels.** Scene 1's grid nailed panels 0-4s but the character suddenly
  faced camera again at 5s even though "seen from behind" was established
  early — the same instruction-drift pattern seen with the Veo video prompts.
  Fix: repeat load-bearing constraints (character orientation, which props
  are visible) explicitly in each panel's own description, not just once at
  the start. **Then also restate the constraint once more as a summary rule**
  after the per-panel list (e.g. "once he turns at 1s, his back stays to the
  camera for every remaining panel until he is fully gone") — this
  redundancy (per-panel + summary) is what actually fixed the drift, not
  either alone.
- **Idioms get taken literally.** "The door starts to crack open" (meaning:
  opens a little) produced actual fracture/damage textures on the door.
  Describe the literal physical state you want ("a narrow gap of light
  shows at the edge") instead of a figure of speech, the same way "furrowed
  brow" got read as an instruction to draw eyebrows on a character with none.
- **Pair the positive description with an explicit negative constraint** for
  anything prone to drifting or being misread — e.g. "the door is simply
  opening on its hinge; it must NOT show any cracks, fractures, or damage,"
  or "the door is STILL OPEN at this point — it has not started closing
  yet." Just describing the desired state isn't as reliable as also naming
  the specific wrong outcome and forbidding it.

## Prompt-writing patterns worth reusing

These are distilled from README.md — read that file for full detail and the
reasoning behind each one, but the short version:

- **FACE LOCK block** in every Nano Banana prompt describing a posed/moving
  character: state exact eye size/shape and explicitly say "NO eyebrows."
  Avoid words like "brow" or "furrow" in expression descriptions — they get
  read as an instruction to draw eyebrows.
- **No unrequested appearance/clothing changes**: state explicitly that body
  proportions/colors/fur must match the reference and no clothing should be
  added unless asked for.
- **Required-change framing**: lead with what must be different from the
  base image, framed as unmistakable and validated with a concrete visual bar
  ("obvious within one second of looking"), before any "keep identical" list.
- **When corrections don't stick**: don't keep patching a flawed generation as
  the new base — reset to the last known-good image and regenerate fresh from
  there. If that also fails after 3-4 different phrasings, it's likely a
  genuine model limitation (compositional/relational reasoning — e.g. "this
  item is attached to that body part, recompute its position after a
  rotation" — is a known weak spot for image-conditioned generation). At that
  point, check whether Flow's own manual edit tools (region select, flip) can
  fix it directly instead of continuing to fight it with prompts.
- **Video CRITICAL RULES**: enumerate the specific failure modes to forbid
  (state reverting, character standing still, props flickering, motion
  repeating), and make ordering constraints between two events explicit
  conditions rather than relying on timing language.
- **Abstract progress rules ("must show visible progress every second") can
  still fail even after adding explicit time caps.** Scene 1 hit this
  twice, in two different beats: first a push action ate half the runway
  despite a numeric cap (fixed by pairing the cap with qualitative-language
  removal, see above), then later — after that fix — the *walking* beat
  stalled near the doorway for 1.5s+ despite an explicit "must move every
  second" rule, because "progress" had no concrete reference point. Fix:
  anchor each second (or half-second) to a landmark actually visible in
  frame (a doormat edge, a threshold line, a railing) — "by 3.5s he must be
  past the threshold line, standing on the landing" is enforceable in a way
  "he must be farther along" is not.
- **A single "turn happens at Xs" instruction doesn't stop the turn from
  leaking earlier.** Even with correct body-orientation logic (see step 2)
  and an explicit single-turn timing rule, a character drifted into a
  side-profile pose a full 2 seconds before the scripted turn, blurring out
  the exact beat (a back-first door push) the timing was meant to protect.
  Fix: pair the "turns once, at Xs" rule with an explicit negative
  constraint repeated at every beat before that point — "at 1s, at 2s: he
  must be fully front-facing, never profile or 3/4 angle" — not just a
  single statement of when the turn is allowed to happen.

## Verifying a generated video

ffmpeg isn't preinstalled in this environment; use the bundled one from
`imageio-ffmpeg` (install once per session if missing):

```bash
pip3 install --quiet --timeout 120 imageio-ffmpeg
FF=$(python3 -c "import imageio_ffmpeg; print(imageio_ffmpeg.get_ffmpeg_exe())")
```

Extract frames at 2fps (0.5s apart) into the scratchpad, then `Read` each one:

```bash
OUT="<scratchpad>/scene_frames"
mkdir -p "$OUT"
$FF -v error -i "<path-to-video.mp4>" -vf "fps=2" "$OUT/frame_%02d.jpg"
```

Walk through every frame in order — don't sample a few. The failures that
matter (door redesigning itself mid-clip, a character momentarily facing the
wrong way, a prop flickering out of existence) tend to show up for only 1-2
frames and are easy to miss if you skip around.

## After finishing a scene

Update `README.md`'s guideline sections with any new failure mode and fix you
discover — this skill and the whole project rely on that file staying current.
Create `scenes/scene-N.md` for the new scene following the structure already
established in `scenes/scene-01.md` (concept, props, status checklist with a
version history, then the three prompts). Commit and push to the working
branch as you go, the same way every step of scene 1 was committed.
