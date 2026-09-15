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
6. **Once both frames are confirmed, ask the user whether to generate a
   storyboard-grid check before writing the video prompt.** Don't just do
   this automatically — always ask first. The point is that Nano Banana
   (images) costs no Flow credits but Veo (video) does, so a free intermediate
   sanity check catches a bad motion plan before it burns a paid generation.
   If they say yes, write a storyboard-grid prompt (see "Storyboard grid" below)
   attaching both confirmed frames as references, have them generate it, and
   review it together. Iterate on the grid (not the actual video prompt yet)
   until the per-second progression looks right — same iteration mindset as
   the frames themselves.
7. **Write the video-connect prompt (Veo 3.1 Lite) from the confirmed
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
8. **After the user shares the generated .mp4, extract frames at ~2fps and
   inspect every one before judging the result** — don't just skim the first
   and last frame. See "Verifying a generated video" below for the exact
   commands. Report findings with timestamps, then decide whether the
   fix is a wording problem in the prompt or a scope problem in the request.

## Storyboard grid (free pre-check before spending Veo credits)

Once start/end frames are confirmed and the user opts in, write a Nano Banana
prompt like this (fill in the bracketed parts from the scene's planned
motion beats):

```
Using the two reference images (the confirmed start frame and confirmed end
frame) plus the motion description below, generate ONE new image: a
storyboard grid of 8 panels arranged in 2 columns x 4 rows, laid out in
reading order (left-to-right, top-to-bottom), representing a snapshot of the
scene at each second from 0 through 7 of an 8-second continuous shot.

Panel order and timing:
- Row 1: 0s (top-left), 1s (top-right)
- Row 2: 2s, 3s
- Row 3: 4s, 5s
- Row 4: 6s, 7s

Each panel shows a small, clearly readable number label in one corner
("0s", "1s", ... "7s") so the sequence is easy to read at a glance.

Panel 0s must match the start reference image exactly. Panel 7s should be
close to the end reference image. The panels in between should show a
plausible, smoothly progressing sequence of this motion:
[short bullet list of the planned story beats, same beats you'd otherwise
put straight into the video prompt]

Camera position/framing, background, and character design must stay
consistent across all 8 panels — this is one continuous scene, not 8
separate images. Thin white borders/gutters between panels are fine so they
don't blend together.

No other text, logos, or watermarks besides the second-number labels.
```

Attach the confirmed start and end frame images as the two references. If the
grid reveals a problem (motion that doesn't fit the timing, an implausible
jump between panels, a pose that doesn't make sense), fix it by regenerating
the grid — this is the cheap place to catch it. Once the user is happy with
the grid, move to writing the actual video-connect prompt (step 7 above),
transcribing each panel's state into the corresponding beat of the motion
description.

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
