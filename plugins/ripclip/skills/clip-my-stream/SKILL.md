---
name: clip-my-stream
description: "Clips a stream or video end to end, from the link to download and editor links. Use when the user runs /ripclip:clip-my-stream."
argument-hint: "[video link or Kick/Twitch channel] [how many clips]"
disable-model-invocation: true
---

Use RipClip to clip this: $ARGUMENTS

1. Ask whether the user owns the video or has permission to use it; set `rights` only after a yes.
2. `import_video` (a channel name means its newest past broadcast), then `job_status` until it gives the `project_id`.
3. `estimate_hu` for the whole video. Tell the user the Horizon Units and wait for a clear yes.
4. `find_clips` with the approved `max_hu` and the number of clips asked for (5 if none).
5. List the clips with titles and timings, play them with `show_clips`, and give download and editor links with `get_download_link`.
