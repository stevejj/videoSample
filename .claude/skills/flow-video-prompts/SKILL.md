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
6. **Write the video-connect prompt** (Veo 3.1 Lite) once both frames are
   confirmed. Keep the motion to at most 2-3 clearly staged beats; if there's
   a single emotional/comedic core action, give it its own loud paragraph
   (e.g. "MOST IMPORTANT MOMENT") rather than letting it blend into a list of
   rules. State hard constraints as CRITICAL RULES, phrased as conditions
   ("X only happens after Y is 100% true"), not as time cues ("near the end").
7. **After the user shares the generated .mp4, extract frames at ~2fps and
   inspect every one before judging the result** — don't just skim the first
   and last frame. See "Verifying a generated video" below for the exact
   commands. Report findings with timestamps, then decide whether the
   fix is a wording problem in the prompt or a scope problem in the request.

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
