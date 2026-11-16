---
name: get-started
description: Explains what the AnyScribe connector can do and how to set it up. Use when the user asks what AnyScribe can do or how to connect it, when their AnyScribe library looks empty, or when an AnyScribe tool says no iPhone or iPad is set up.
---

# Get started with AnyScribe

AnyScribe is an iPhone and iPad app that transcribes YouTube videos, podcasts, TikTok and Instagram clips, lectures, voice memos and recordings. The AnyScribe connector gives you access to the user's own AnyScribe library.

## What you can do with it

- Search the user's transcripts and highlights (`search_library`).
- List transcriptions, newest first, by folder or date (`list_transcriptions`), and list folders (`list_folders`).
- Read a transcript, summary, description or translation (`get_transcription`). Long transcripts come in pages; follow `next_cursor` until it is null.
- List the passages the user highlighted (`list_highlights`).
- Send a public link to the user's iPhone or iPad to transcribe (`transcribe_link`) and follow it (`get_transcription_status`).

The library tools only read. Nothing can be edited or deleted through the connector.

## What the user needs

- The AnyScribe app on iPhone or iPad, signed in, with Cloud Sync turned on. Only synced items are visible to the connector.
- When connecting, they sign in with the same Apple ID or email they use in the app and choose Allow.
- To send links from the chat: open AnyScribe on the iPhone, go to AI assistants once (tap the balance at the top), and allow notifications. Transcribing a link uses the account's AnyScribe transcription time, the same as adding the link in the app.

## When something doesn't work

- **The library is empty or an item is missing:** Cloud Sync is off, or the item hasn't synced yet. Ask the user to open AnyScribe and check Cloud Sync.
- **"No iPhone or iPad is set up to receive links":** the user should open AnyScribe on their iPhone, sign in with the same account and open AI assistants once.
- **A link stays queued:** the iPhone may be offline or didn't get the notification. Opening AnyScribe on the iPhone starts it.

## Good first prompts to suggest

- "What did I transcribe this week? Give me the three most useful takeaways."
- "Search my AnyScribe library for spaced repetition and summarize what each talk says about it."
- "Transcribe this YouTube link in AnyScribe and summarize it when it's done."

Docs: https://www.anyscribe.app/mcp
