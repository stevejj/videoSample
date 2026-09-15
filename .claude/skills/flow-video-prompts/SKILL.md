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
   - **Ask which Flow generation mode the user wants: "Frames to Video" or
     "Ingredients to Video" ("소재").** They write differently. Frames to
     Video auto-interpolates between the start/end images, so the prompt
     only needs to describe the motion between them. Ingredients mode gives
     no such guarantee — the reference images (which can now include the
     storyboard grid itself as a third image) are style/staging references
     only, so the prompt must explicitly state that the video's opening and
     closing frames must match reference images 1 and 2, and must explain
     each reference image's role (1st = opening frame, 2nd = closing frame,
     3rd = per-second storyboard grid to follow, staged as smooth continuous
     motion rather than jumping between the 8 panels). Ingredients mode's
     upside is that the grid — already validated second-by-second — becomes
     a much stronger anchor than describing the same beats in text alone.
   - **Before reusing a previously-confirmed reference image (especially a
     storyboard grid) in a new context, re-check it against every logic fix
     found since it was confirmed.** Scene 1's grid was confirmed before the
     body-orientation contradiction in step 2 was discovered and fixed in
     the video prompt — the grid's own panels still depicted the disproven
     "already turned around, pushing with the back" pose. That was harmless
     while the grid was only a human sanity-check, but became a real risk
     once ingredients mode would feed the grid directly into video
     generation: reference images are known to outweigh text instructions
     (see the prop left/right mirroring failures), so a stale grid could
     drag the video back into the exact orientation bug the text was trying
     to prevent. Regenerating the grid (free) to match the current, corrected
     script is worth doing before it becomes a direct generation input.
9. **After the user shares the generated .mp4, extract frames at ~2fps and
   inspect every one before judging the result** — don't just skim the first
   and last frame. See "Verifying a generated video" below for the exact
   commands. Report findings with timestamps, then decide whether the
   fix is a wording problem in the prompt or a scope problem in the request.

## Storyboard grid (free pre-check before spending Veo credits)

Once start/end frames are confirmed and the user opts in, write a Nano Banana
prompt like this (fill in the bracketed parts from the scene's planned
motion beats). This template already bakes in every fix scene 1 needed
across 3 grid iterations (v5→v7) — start from this shape, don't start from
a bare bullet list and rediscover the same failure modes:

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

CAMERA LOCK (applies to every single panel, no exceptions): the camera
framing, distance, angle, and zoom level are IDENTICAL in all 8 panels —
exactly matching panel 0s. [Name 2-3 fixed background elements that appear
in the shot, e.g. a shoe rack, a doormat, a door frame] must appear at the
exact same size, scale, and position in every panel without exception. Do
not let the shot zoom in, zoom out, crop tighter, or shift at any point
across the 8 panels — only [character]'s pose and position change, never
the camera.

Panel 0s must match the start reference image exactly. Panel 7s should be
close to the end reference image. In every panel, the character's face, fur
color/texture, and proportions must match the character reference image —
do not let appearance drift across panels. The panels in between should
show a plausible, smoothly progressing sequence of this motion:
[per-panel bullet list of the planned story beats, same beats you'd
otherwise put straight into the video prompt — for each beat, follow the
positive+negative pairing pattern below rather than a bare description]

The N → N+1 → ... stretch covering [the exit/transition beats] is one
single, continuous progression, not disconnected snapshots — position,
stride, and any framing crop should progress smoothly and believably
between consecutive panels, like flipping through frames of one real
sequence rather than picking unrelated moments.

Camera position/framing, background, and character design must stay
consistent across all 8 panels — this is one continuous scene, not 8
separate images (see CAMERA LOCK above). Thin white borders/gutters
between panels are fine so they don't blend together.

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
is happy with the grid, move to writing the actual video-connect prompt
(step 8 above), transcribing each panel's state into the corresponding beat
of the motion description.

**Writing each panel's motion beat — do this by default, not just when a
first attempt fails** (scene 1 needed 3 grid rounds to converge on this;
starting here skips straight to what worked):

- **Pair every positive description with an explicit negative constraint,
  AND back the negative with a concrete positive detail of what must stay
  visible/intact.** A negative constraint alone ("must NOT be shown in
  profile," "must NOT show cracks or damage") is not reliable by itself —
  scene 1 saw the model default to "already turned away" and "damaged
  surface" for a hard-push beat even when both were explicitly forbidden
  in text, twice, on two different grid attempts. What worked: naming the
  exact feature that must remain visible ("both eyes and his beak must be
  clearly visible, same as the opening panel") and the exact surface state
  that must be unchanged ("identical smooth brown paint, matching the
  closed-door panel exactly") — a positive anchor, not just a prohibition.
- **Repeat load-bearing constraints (orientation, visible props) in every
  panel's own description, not just once at the top**, and **restate the
  constraint once more as a summary rule** after the per-panel list (e.g.
  "once he turns at Xs, his back stays to the camera for every remaining
  panel until he is fully gone"). A constraint stated once doesn't reliably
  carry across 8 panels — the redundancy (per-panel + summary) is what
  fixed the drift, not either alone.
- **Never use idioms for a physical state** — "the door starts to crack
  open" (meaning: opens a little) produced actual fracture/damage textures.
  Describe the literal physical state instead ("a narrow gap of light
  shows at the edge"), the same way "furrowed brow" got read as an
  instruction to draw eyebrows on a character with none.
- **The CAMERA LOCK block in the template above is not optional decoration
  — include it by default.** Without a framing anchor tied to fixed
  background elements, panel-to-panel zoom/distance can drift even when
  nothing else is wrong with the prompt.

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

## Video-connect prompt building blocks (default, not just for failures)

These converged after several rounds on scene 1 (v9→v13) — start a new
scene's video prompt with these already in place rather than adding them
after a failed attempt shows why they're needed:

- **If a confirmed storyboard grid exists and the user is generating in
  Flow's "Ingredients to Video" ("소재") mode, wrap the prompt to name each
  reference image's role explicitly** — mode doesn't auto-interpolate
  between a start/end image pair the way "Frames to Video" does, so the
  prompt has to state it:
  ```
  Using the three uploaded reference images as the basis for this video:
  - The FIRST image is the exact opening moment of this video. The video
    must begin matching it essentially exactly.
  - The SECOND image is the exact final moment of this video. The video
    must end matching it essentially exactly.
  - The THIRD image is an 8-panel storyboard grid (labeled 0s-7s) that
    shows exactly what happens in every second in between. Treat this
    grid as the authoritative second-by-second script — reproduce its
    poses/framing/positions at their labeled seconds, staged as smooth
    continuous motion rather than jumping between panels.
  ```
  Ask which mode the user is using before writing the prompt — Frames to
  Video (just describe the motion between the two images) and Ingredients
  mode (the wrapper above, plus the grid as a third reference) need
  differently-shaped prompts, and defaulting to the wrong shape wastes a
  paid Veo generation.
- **Anchor multi-second movement to landmarks visible in frame, not
  relative progress language.** "He must show visible progress every
  second" was stated explicitly and still produced a 1.5s+ stall at a
  doorway threshold. What worked: tying each second to something actually
  in the shot ("by 3.5s he must be past the threshold line, standing on
  the landing," "by 4s, at the same depth as the railing"). Pick 2-3 fixed
  landmarks in the scene's background and check off a checkpoint against
  them for every second of a multi-second move.
- **Before a scripted one-time orientation change (a single turn, a
  reveal), lock every earlier beat with its own positive+negative
  orientation pair** — not just a statement of when the change is allowed
  to happen. "He turns once, at 3s" did not stop the turn from leaking to
  1s in practice; "at 1s, at 2s: he must be fully front-facing, both eyes
  and beak visible, never profile or back-view" at each of those beats is
  what actually held it.
- **Give the single emotional/comedic core action its own loud paragraph**
  (e.g. "MOST IMPORTANT MOMENT") separate from the CRITICAL RULES list, and
  cap it with an explicit numeric deadline ("must be finished by Xs") — a
  qualitative emphasis like "give this weight, don't rush it" will win
  against a numeric cap stated elsewhere in the prompt and eat the rest of
  the clip's runway.

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
