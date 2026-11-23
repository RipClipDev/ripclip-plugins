---
name: edit-clips
description: "Edits finished clips and photos in RipClip from plain requests. Use when the user wants bigger or recolored captions, silences or filler words cut, swear words bleeped, picture-in-picture or a green screen removed, clips joined into one video, music, a title, a facecam split, a trim, a color grade, filters, effects, transitions, speed, a different shape, text, stickers, sound effects, or subtitles in another language; a brighter, warmer or punchier look; zoom, mirror or reframing; a part slowed down, frozen or cut out; the original sound muted or cleaned up; a photo brightened; or the last edit undone, and then wants to see the result. Every edit is free and can be undone. Not for cutting new clips from a long video or for posting."
---

# Edit clips

Find the clip with `list_clips` (newest first) unless the user gave one. Set only what the user asked for.

| The user asks for | Call |
|---|---|
| Caption size, color, position or animation, uppercase, remove silences or "ums", music, a title at the top, a facecam split, zoom, emojis, a trim, bleep or mute swear words (`bleep`) | `edit_clip`; `also_clip_ids` does the same to up to 20 more clips in one call |
| A caption look, font, outline, color grade or filter, an effect, a transition, speed, fade, a square or 4:5 shape, a progress bar | `style_clip` |
| Text, a sticker or emoji, a sound effect at a time, another video in a corner (`pip_clip_id`) with its green screen removed (`green_screen`) | `add_to_clip` |
| Several clips joined into one highlights video | `combine_clips` (in the order given; a new clip, the originals stay) |
| Subtitles in another language, bilingual or replaced | `translate_captions` |
| Brighter, darker, warmer, punchier, black and white, one color richer (whole clip, a part, or a photo) | `adjust_look` |
| Zoom, show more of one side, mirror, the whole picture with a blurred or colored background, a custom size | `frame_clip` |
| Slow down or speed up one part, freeze a frame, cut a part out | `retime_clip` |
| Mute or turn up the original sound, remove noise, clearer voice, even loudness, a voice effect, music level or ducking | `mix_audio` |
| "Undo that" | `undo_edit` (calling again steps further back) |
| "Brighten this photo" with a link or an attached picture | `import_photo`, then `adjust_look` on the photo id `job_status` gives |
| "What styles are there?" | `edit_catalog` (the names `style_clip` and `add_to_clip` take) |

Each edit returns a `job_id`: poll `job_status` until it is done, then call `preview_frame` and show the user the picture, and give the `editor_url`. Each edit replaces the clip's video (or the photo's picture) with the new render and is saved as a version `undo_edit` can take back; edits cost no Horizon Units. `adjust_look` takes set values, not steps, and its notes say the look now, so "a bit more" adds to that. Saved photos are `list_clips` with `kind` photos; `get_download_link` gives the edited picture. If a tool refuses an option for the account, say which option and move on.
