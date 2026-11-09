---
name: post-clips
description: Writes captions and saves post drafts for clips in RipClip. Use when the user wants a caption or hashtags for TikTok, YouTube Shorts, Instagram Reels, Facebook, Threads, X or Bluesky, wants a clip put on the posting calendar for a day and time, wants a week of posts planned, or wants to change or delete a draft. Saves drafts only: the user reviews and schedules each one in RipClip. Not for editing the video or reading results.
---

# Draft posts

RipClip saves drafts. It never publishes or schedules a post on its own, so never tell the user a post is live or scheduled: say it is a draft and give the `review_url` where they check it and schedule it.

1. Find the clip with `list_clips`. `list_social_accounts` shows the connected accounts and their `account_id`; its `note` says which platforms can post yet.
2. Captions: `write_captions` (up to 5 platforms, optional `tone`) writes one per platform within that platform's limits and saves nothing. Show them and let the user choose.
3. One post: `draft_post` with `clip_id`, `platform` (tiktok, youtube, instagram, facebook, threads or bluesky; "Shorts" and "Reels" work; X is coming soon, so it is refused), the chosen `caption`, and `scheduled_at` in ISO 8601 with its offset when the user named a time. One call per platform.
4. A week: `plan_posts` with `platforms`, `count` and the user's IANA `timezone` drafts the highest-scoring unposted clips at the times the user's own posts do well. `best_time_to_post` shows where those times come from.
5. Changes: `get_post_stats` with `status` "draft" lists drafts and their `post_id`; `update_draft` changes the caption, time, platform or TikTok options; `delete_draft` moves a draft to Deleted posts (restorable for 30 days). Posts already scheduled or posted are refused. `show_drafts` shows the calendar in the chat.

For YouTube the first line of the caption is the title (100 characters). Instagram allows 5 hashtags, X 280 characters, Threads 500.
