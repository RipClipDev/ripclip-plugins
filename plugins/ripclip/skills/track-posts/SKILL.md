---
name: track-posts
description: "Reports how posts made through RipClip performed. Use when the user asks how their clips or videos are doing, how last week went, which platform works for them, when to post, whether anything is taking off, why some posts did better, how many followers they gained, or what to post next. Reads only; never changes posts. Not for editing clips or writing drafts."
---

# Track posts

Pick the tool for the question, then say what the numbers do and do not show.

| The user asks | Call |
|---|---|
| "How did last week go?" "What should I post next?" | `weekly_report` (add `show_report` to draw it) |
| "How is this post doing?" "Which TikTok took off?" | `get_post_stats` |
| "Which platform is working?" | `compare_platforms` |
| "Is anything blowing up?" | `whats_taking_off` |
| "What do my better posts have in common?" | `why_it_worked` |
| "When should I post?" | `best_time_to_post` |
| "How many followers did I gain?" | `get_account_stats` |

Always pass the user's IANA `timezone` where a tool takes one. Platforms count views differently, so compare each with its own history and never add them up; `null` means the platform sent no such count. `why_it_worked` shows differences in the data, not causes, and says so when there are too few posts. Only posts made through RipClip are covered. To act on `post_next`, offer `plan_posts`.
