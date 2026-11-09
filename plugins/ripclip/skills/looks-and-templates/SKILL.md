---
name: looks-and-templates
description: "Saves and reuses the look of clips in RipClip. Use when the user wants to keep a look to use again (\"save this style\", \"make this my template\", \"edit it like last time\"), wants every new clip to get a look automatically, wants their clips to look like a TikTok or YouTube clip they link, or wants a saved template or clipping preset put on other clips. Not for a one-off caption or color change, or for cutting new clips."
---

# Looks and templates

A template holds a clip's whole edit (format, captions, color, effects, transitions, music, text and sounds). A clipping preset holds the format and caption look RipClip puts on clips as it finds them; the default one goes on every new clip.

| The user asks | Call |
|---|---|
| "Save this style", "make this my template" | `save_template` with `clip_id` and `name` |
| "Clip my streams like this from now on" | `save_template` with `for_new_clips` true: it also becomes the default clipping preset, so every clip `find_clips` or `clip_range` makes gets the look |
| "Make my clips look like this" with a TikTok or YouTube link | `save_template` with `look_from` (the link) and a `name`, no `clip_id`; add `for_new_clips` when the user wants it on every new clip |
| "Edit it like last time", a saved template on a clip | `style_clip` with `template` (a name or id); `template_parts` limits it to some parts |
| A saved clipping preset on finished clips | `style_clip` with `clipping_preset`; `also_clip_ids` takes up to 49 more clips |
| "What looks have I saved?" | `edit_catalog` with kind "templates", and `list_clipping_presets` |

`look_from` reads the captions and layout from the linked clip's cover picture, so say what the `note` reports it read and that the preset can be changed in RipClip under Clipping presets. Saving costs no Horizon Units. A look put on a clip renders a new version: poll `job_status`, show it with `preview_frame`, and `undo_edit` takes it back. If a tool refuses an option for the account, say which option and move on.
