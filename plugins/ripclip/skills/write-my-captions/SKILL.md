---
name: write-my-captions
description: "Writes a caption per platform for the newest clip and saves the chosen ones as drafts. Use when the user runs /ripclip:write-my-captions."
argument-hint: "[platforms]"
disable-model-invocation: true
---

Use RipClip to write captions for the newest clip on: $ARGUMENTS (TikTok, YouTube Shorts and Instagram Reels if none are named)

Find the clip with `list_clips`, then `write_captions` for those platforms. Show each caption (and the YouTube title) and ask which to keep. Only then save the chosen ones as drafts with `draft_post`. Nothing is posted.
