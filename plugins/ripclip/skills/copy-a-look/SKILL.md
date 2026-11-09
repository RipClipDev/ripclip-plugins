---
name: copy-a-look
description: Copies the caption and layout look of someone else's TikTok or YouTube clip into a clipping preset. Use when the user runs /ripclip:copy-a-look.
argument-hint: "[TikTok or YouTube link] [name]"
disable-model-invocation: true
---

Use RipClip to copy the look of this clip: $ARGUMENTS

Call `save_template` with `look_from` set to the link and `name` set to the name given (or "Copied look"). Ask whether every new clip should get it; if yes, pass `for_new_clips` true. Tell the user what the `note` says was read, and that the preset can be changed in RipClip under Clipping presets. To put it on clips already made, offer `style_clip` with `clipping_preset`.
