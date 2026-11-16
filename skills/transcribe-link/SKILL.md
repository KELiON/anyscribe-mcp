---
name: transcribe-link
description: Sends a video, podcast or audio link to the user's iPhone to transcribe with AnyScribe, follows the job and works with the transcript once it's ready. Use when the user shares a YouTube, TikTok, Instagram, X, Vimeo or podcast link and asks to transcribe it, save it to AnyScribe, or summarize it through AnyScribe.
---

# Transcribe a link with AnyScribe

## 1. Send it

- Use a public http or https link to a single video, episode or audio file. Files on the user's computer can't be sent.
- Sending a link uses the user's AnyScribe transcription time. If the user only asked about the link and didn't ask to transcribe it, check first.
- Call `transcribe_link` with the `url`. Keep the `job_id` and tell the user the link went to their iPhone.

## 2. Follow it

- Call `get_transcription_status` with the `job_id`. Status is `queued`, `transcribing`, `completed` or `failed`, with progress while it runs.
- The work happens on the user's iPhone, so it usually takes a few minutes and longer for long recordings. Share the progress and check again later instead of calling the tool in a tight loop.
- If it stays `queued`, the iPhone may be offline or missed the notification. Opening AnyScribe on the iPhone starts it.

## 3. Use the result

- When the status is `completed`, take the `transcription_id` and call `get_transcription`, following `next_cursor` until it is null.
- Then do what the user asked: a summary, a brief, quotes, a translation or answers to questions.

## If it fails

Pass on the error message as written. The common cases:

- **No iPhone or iPad is set up:** the user should open AnyScribe on their iPhone, sign in with the same account and open AI assistants once.
- **Out of transcription time:** the user can add time in the AnyScribe app.
- **The link can't be transcribed** (private, removed, or not a media page): ask for another link.
