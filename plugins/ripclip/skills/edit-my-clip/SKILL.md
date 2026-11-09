---
name: edit-my-clip
description: "Changes the newest clip, or the one named, by describing the change. Use when the user runs /ripclip:edit-my-clip."
argument-hint: "[what to change]"
disable-model-invocation: true
---

Use RipClip to edit the newest clip (or the one named): $ARGUMENTS

Find it with `list_clips`. Change only what was asked, with the tool that does it: `edit_clip` (caption size and color, silences, filler words, music, title, layout, trim), `style_clip`, `add_to_clip`, `adjust_look`, `frame_clip`, `retime_clip` or `mix_audio`. Wait for the render with `job_status`, show it with `preview_frame` and give the editor link. `undo_edit` takes it back.
