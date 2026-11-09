---
name: find-top-moments
description: Searches a stream or video for its top moments, or the moments about one topic, and clips the ones the user picks. Use when the user runs /ripclip:find-top-moments.
argument-hint: "[video link or channel] [topic]"
disable-model-invocation: true
---

Use RipClip to find the top moments in this video: $ARGUMENTS

1. Confirm the user owns it or has permission. `import_video`, then `job_status` until it gives the `project_id`.
2. `estimate_hu` for the whole video and ask before spending anything.
3. With a topic: `find_moments` for it, `get_moments`, and show each time and quote so the user can choose; cut the chosen ones with `clip_range` (or `find_clips` with `topic` for several). Without a topic: `find_clips` for a few.
4. When the clips are ready, `explain_clips`: say which one to post first and why, with download and editor links.
