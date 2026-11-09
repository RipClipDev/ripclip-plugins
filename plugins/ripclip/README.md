# RipClip for Claude

RipClip turns long videos (Twitch and Kick streams, VODs, podcasts, video links) into captioned vertical clips, edits them, saves post drafts for TikTok, YouTube Shorts, Instagram Reels, Facebook, Threads and Bluesky, and tracks how the posts do. This plugin connects Claude to a RipClip account so all of that works from the chat.

## What is inside

- **The RipClip connection** (`.mcp.json`): one remote server, `https://ripclip.org/mcp/`, with RipClip's tools for clipping, editing, posting and tracking. You sign in to RipClip and choose its permissions and a monthly Horizon Unit limit when you connect.
- **Skills** that teach Claude to use those tools well: clip videos, edit clips, looks and templates, post clips, track posts.
- **Shortcuts** you can type in Claude Code and Cowork, such as `/ripclip:clip-my-stream`, `/ripclip:edit-my-clip`, `/ripclip:copy-a-look`, `/ripclip:plan-my-week` and `/ripclip:how-are-my-posts-doing`.
- **An agent**, `clip-producer`, that takes one video from import to post drafts (Claude Code and Cowork).

## Install

In Claude, find RipClip under Plugins, Discover, and add it. In Claude Code:

```
/plugin marketplace add RipClipDev/ripclip-plugins
/plugin install ripclip@ripclip-plugins
```

## Data handling

The plugin talks to one place: RipClip's server at `https://ripclip.org/mcp/`, over a sign-in you approve (OAuth). It sends what you ask Claude to do there: video links to import, clip edits, captions and post drafts. It contains no hooks, no programs and no other network destinations. RipClip saves drafts only and never publishes a post by itself. Work that uses Horizon Units is quoted first and runs only after you approve it.

- Documentation: https://ripclip.org/ai-assistants
- Privacy: https://ripclip.org/privacy
- Terms: https://ripclip.org/terms
- Support: https://ripclip.org/support (support@ripclip.org)
