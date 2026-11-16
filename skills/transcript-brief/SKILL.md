---
name: transcript-brief
description: Turns something the user transcribed in AnyScribe into a brief with key points, quotes and open questions, or compares what several transcripts say about a topic. Use when the user asks to summarize, recap, brief or quote a video, podcast, lecture or voice memo from their AnyScribe library.
---

# Brief from an AnyScribe transcript

## 1. Find the transcription

- If the user names a title, person or topic, call `search_library` with one to three distinctive words. Every word must appear as a whole word, so short queries find more.
- If they refer to time ("this week", "my latest podcast"), call `list_transcriptions`, newest first, with `since` set to the start of that period.
- If several items match and the right one isn't obvious, show the titles and dates and ask which one.

## 2. Read all of it

- Call `get_transcription` with the id and `part` set to `transcript`. While `next_cursor` is not null, call it again with that cursor. Don't brief from the first page alone.
- If the user only wants the gist, the stored summary (`part: "summary"`) is faster. Say that it's the app's summary.
- For another language, check `translations_available` and use `part: "translation"` with that `language`.
- Call `list_highlights` with the `transcription_id`. Highlights are the passages the user marked as important, so give them weight.

## 3. Write the brief

- One line on what it is: title, source, date and length.
- Three to seven key points, in the order they come up.
- Two or three short quotes, copied exactly from the transcript.
- Action items or open questions, if there are any.
- The source link (`source_url`) and the AnyScribe link (`open_url` or `share_url`) when present.

Quote only what the transcript says. Transcripts come from speech recognition, so names and numbers can be misheard; say so when a point depends on one.

## Comparing several transcriptions

Search, read each item in full, then write a short section per item followed by what they agree and disagree on.
