# RipClip

The `ripclip` MCP server connects to the user's RipClip account (https://ripclip.org). The first call opens RipClip's
sign-in in the browser, where the user picks the permissions and a monthly Horizon Unit (HU) limit.

- Clip: `import_video` takes a Kick or Twitch VOD or clip link, an Apple Podcasts episode, a Drive, Dropbox or OneDrive
  share link, or a direct video file link (not YouTube links, not a stream that is still live). Run `estimate_hu`, show
  the user the cost, and call `find_clips` only after they approve it.
- Edit: `edit_clip`, `style_clip`, `translate_captions` and the other edit tools render a new version each time;
  `undo_edit` goes back. `get_download_link` and the editor link hand the clip to the user.
- Post: `draft_post` and `plan_posts` save drafts only. RipClip never publishes from here; the user schedules drafts in
  RipClip.
- Track: `get_post_stats`, `whats_taking_off`, `weekly_report` and `best_time_to_post` read the user's own posts.

Only use videos the user owns or has permission to use.
