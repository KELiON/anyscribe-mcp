# AnyScribe for AI assistants

AnyScribe is an iPhone and iPad app that transcribes YouTube videos, podcasts, TikTok, Instagram, lectures, voice memos and recordings. This repository holds the files that connect AnyScribe to ChatGPT, Claude, Cursor and other apps that support the Model Context Protocol (MCP). The server is hosted by AnyScribe, so there is nothing to install or run.

- **Server URL:** `https://mcp.anyscribe.app` (Streamable HTTP, OAuth sign-in with your Apple ID)
- **Docs:** https://www.anyscribe.app/mcp
- **App:** [AnyScribe on the App Store](https://apps.apple.com/app/id6758009667)

## What your assistant can do

- Search your transcripts and highlights
- Read transcripts, summaries and translations, page by page when they're long
- List your transcriptions, folders and highlights
- Send a link to your iPhone or iPad to transcribe, and follow its progress

Library tools are read-only, so an assistant can't change or delete anything. Sending a link adds a new transcription, the same as sharing a link to AnyScribe yourself, and uses your transcription time.

## Before you connect

- AnyScribe on iPhone or iPad, signed in with Apple, with Cloud Sync on.
- To transcribe links from an assistant, open AI assistants in the app once (tap your balance) and allow notifications.

## Connect

**Claude** (web, desktop and mobile): Settings → Connectors → Add custom connector. Name it AnyScribe, paste the server URL, choose Add, then Connect. Sign in with your Apple ID and choose Allow.

**ChatGPT:** Settings → Apps → Advanced settings → turn on Developer mode. Back in Apps, choose Create, name it AnyScribe, paste the server URL and pick OAuth. Sign in and choose Allow, then turn AnyScribe on from the + menu in a chat.

**Claude Code:**

```sh
claude mcp add --transport http anyscribe https://mcp.anyscribe.app
```

Then type `/mcp` and sign in. Or install it as a plugin:

```
/plugin marketplace add KELiON/anyscribe-mcp
/plugin install anyscribe@anyscribe
```

**Cursor:** [Add to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=anyscribe&config=eyJ1cmwiOiJodHRwczovL21jcC5hbnlzY3JpYmUuYXBwIn0%3D), or add the server URL under Settings → MCP.

**Kiro:** [Add to Kiro](https://kiro.dev/launch/mcp/add?name=anyscribe&config=%7B%22url%22%3A%22https%3A%2F%2Fmcp.anyscribe.app%22%7D), then sign in when Kiro asks.

**VS Code:**

```sh
code --add-mcp '{"name":"anyscribe","type":"http","url":"https://mcp.anyscribe.app"}'
```

**Other clients:** add a remote MCP server with this configuration. Sign-in is discovered from the server.

```json
{
  "mcpServers": {
    "anyscribe": { "url": "https://mcp.anyscribe.app" }
  }
}
```

## Example prompts

- What did I transcribe this week? Give me the three most useful takeaways.
- Search my AnyScribe library for "spaced repetition" and summarize what each talk says about it.
- Transcribe https://www.youtube.com/watch?v=dQw4w9WgXcQ in AnyScribe and summarize it when it's done.

## Privacy

- Assistants only see your library after you sign in and choose Allow, and only the account you signed in with.
- Your library copy is encrypted inside each database row. The server decrypts only what a tool asks for and sends it to the assistant.
- Links an assistant sends are kept in your account with the assistant's name and status, so you can see them under AI assistants.
- Disconnect an assistant in its settings or in AnyScribe under AI assistants. To delete the copy, turn off Cloud Sync and choose Remove from Cloud.

Full policy: https://www.anyscribe.app/privacy#ai-assistants

## Support

support@anyscribe.app · https://www.anyscribe.app/support

## License

The files in this repository are MIT licensed. The AnyScribe app and server are not open source.
