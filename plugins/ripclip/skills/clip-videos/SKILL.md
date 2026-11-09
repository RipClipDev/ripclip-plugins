---
name: clip-videos
description: "Turns long videos into short vertical clips with RipClip. Use when the user wants to clip a Twitch or Kick stream or VOD, turn a podcast episode or a video link into shorts or TikToks, find the highlights or one topic in a long video, or cut an exact time range. Imports the video, quotes the cost in Horizon Units and cuts clips only after the user approves. Not for editing a finished clip, writing or scheduling posts, or checking views."
---

# Clip long videos

1. Get the video. Call `import_video` with `url` (a Kick or Twitch VOD, highlight or clip link, an Apple Podcasts episode, a Google Drive, Dropbox or OneDrive share link, or a direct video link), or with `channel` and `platform` ("kick" or "twitch") for a streamer's newest past broadcast. Set `rights` to true only after the user says they own the video or have permission. Use a stable `request_key`. Poll `job_status` until it gives the `project_id`. If the user names no source, call `list_projects` and offer what is already imported.
2. Quote the cost. Call `estimate_hu` for that project, tell the user the Horizon Units, and wait for a clear yes. Do not call `find_clips`, `find_moments` or `clip_range` before the user approves. Pass the approved number as `max_hu`.
3. Pick the tool for the request:
   - Highlights from the whole video: `find_clips` with `count`; add `topic`, `min_seconds` and `max_seconds`, a saved look from `list_clipping_presets`, or switches (filler words, pauses, auto emojis, auto zoom) only when the user asked.
   - A topic or a moment by meaning ("where do I talk about the new patch"): `find_moments`, then `get_moments`; let the user choose, then `clip_range` for one or `find_clips` with `topic` for several.
   - An exact stretch ("1:02:10 to 1:03:00"): `clip_range` with `start_seconds` and `end_seconds`.
4. Poll `job_status`, then `list_clips`. `explain_clips` says why each clip was picked and which to post first; its score ranks clips against each other and is not a view forecast. `show_clips` plays them in the chat; `get_download_link` gives the file and the editor link. `list_library` lists every rendered file saved in the account and `search` finds one by words in its title.

Limits to state plainly: YouTube links are not supported (the user uploads the file in RipClip); a stream that is still live cannot be clipped until it ends.
