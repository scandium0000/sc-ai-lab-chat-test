
# Sc Chat — Android 0.6.0

<p align="center">
  <img src="app/src/main/assets/logo.png" width="112" alt="Sc Ai Lab atom emblem">
</p>

<p align="center">
  <strong>A focused, multi-provider AI workspace by Sc Ai Lab.</strong>
</p>

<p align="center">
  Android · Local-first · Provider-independent · 0.6.0
</p>

---

## Overview

**Sc Chat** is an Android AI chat application developed by **Sc Ai Lab**. It brings conversations, projects, personal assistants, model connections, and conversation attachments into one mobile workspace.

The interface uses its own Sc Ai Lab identity, blue accent system, atom emblem, page structure, and local-first workflow.

The application is designed to remain independent of any single model provider. The current implementation supports Pollinations and user-configured OpenAI-compatible chat-completions endpoints.

## Highlights

### Chat Workspace
- Streaming assistant responses.
- Stop generation.
- Copy messages, edit previous user prompts, and regenerate assistant responses.
- Markdown rendering, including headings, lists, tables, links, code blocks, and code-copy actions.
- Image and document attachments in conversations.
- Android keyboard resizing support.

### Projects
- Create, edit, and delete local projects.
- Create conversations inside a project.
- Move existing conversations into or out of projects.
- View conversations belonging to a project.
- Deleting a project does not delete its conversations.

### Personal Assistants
- Create, edit, select, and delete local assistants.
- Define assistant-specific system instructions.
- Associate conversations with an assistant.

### Models & Connections
- Pollinations device authorization flow.
- User-configurable OpenAI-compatible HTTPS providers.
- Provider selection and model selection.
- Per-provider Vision capability setting.
- API credentials stored through the Android Keystore bridge with AES-GCM encryption.
- Pollinations model discovery uses conservative pricing checks.

### File Library
- Aggregates images and documents attached to saved conversations.
- Search attachments by filename or conversation title.
- Navigate back to the conversation containing an attachment.
- On-device text extraction for text-based PDFs.
- Scanned image-only PDFs are not OCR processed.

### Account & Appearance
- Local registration and login.
- Profile image and display-name editing.
- Password changes after current-password verification.
- Account deletion for the current device.
- Automatic light/dark theme based on Android system appearance.
- Blue Sc Ai Lab accent color and atom emblem.

## Navigation

| Section | Purpose |
|---|---|
| Conversations | Chat history and new conversations |
| Projects | Group related conversations |
| AI Assistants | Manage custom assistant instructions |
| Models & Connections | Configure providers and models |
| File Library | Find conversation attachments |
| Account & Settings | Manage local profile and preferences |

## Requirements

- Android 8.0 (API 26) or later.
- Internet connection for remote AI providers.
- Valid provider credentials where required.
- An OpenAI Chat Completions-compatible endpoint for custom providers.

## Installation from GitHub Actions

1. Upload `ScChat_0.6.0.zip` to the root of the GitHub repository.
2. Put the provided workflow at `.github/workflows/build-from-zip.yml`.
3. Run **Build Sc Chat 0.6.0 APK** from the Actions page.
4. Download the `ScChat-0.6.0-debug` artifact after a successful build.
5. Install `app-debug.apk` on your Android device.

The current build is a debug/test APK, not a production release.

## Build from Source

Requirements:

- JDK 17.
- Android SDK Platform 35.
- Android Build Tools 35.0.0.
- Gradle 8.9.

From the `ScChat_Android` directory:

```bash
gradle --no-daemon :app:assembleDebug
```

The APK is generated at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## Custom Provider Configuration

Open **Models & Connections → Add OpenAI-compatible provider** and enter:

- Provider display name.
- HTTPS API Base URL.
- Model ID.
- API Key.
- Whether the selected model supports image input.

Example configuration:

```text
Provider Name: My Provider
Base URL: https://api.example.com/v1
Model ID: example-model
API Key: your-provider-key
```

These values are illustrative only.

Provider pricing, quotas, model capabilities, and data handling are determined by the provider, not by Sc Chat.

## Local Data & Privacy

- User accounts, profile data, projects, assistants, conversations, and attachments are stored locally.
- The local account system does not provide cloud access, password recovery, or cross-device synchronization.
- Provider API credentials are handled through the native Android Keystore bridge.
- Attachments and prompts are sent to the selected AI provider when submitted.
- The File Library indexes attachments stored inside local conversations; it is not a separate cloud drive.
- Avoid uploading passwords, private credentials, or unnecessary personal information.

## Compatibility & Upgrade Notes

- Android `applicationId` remains `ai.scailab.chat`.
- Internal local-storage namespaces remain `scailab.*` to preserve compatible previous-version data.
- Keep the development signing key stable for test updates.
- Do not use the development signing key for a public production release.
- If Android reports a signing-certificate conflict, back up local data before considering an uninstall.

## Roadmap

- [x] Local accounts and profile settings
- [x] Streaming chat and message actions
- [x] Custom AI assistants
- [x] Multi-provider connection architecture
- [x] Projects and project-linked conversations
- [x] Local attachment library
- [x] Automatic system light/dark theme
- [ ] Conversation memory and context management
- [ ] Knowledge collections and RAG
- [ ] Voice input and speech output
- [ ] HSSM native provider integration
- [ ] Encrypted local conversation database and backups

## About Sc Ai Lab

Sc Chat is part of the Sc Ai Lab ecosystem. The long-term direction is to provide one flexible client for third-party cloud models, local inference runtimes, and Sc Ai Lab's own HSSM models.

## Disclaimer

Sc Chat is under active development. This version is intended for testing. Compatibility and provider integrations may change between versions.

Verify provider pricing and privacy policies before sending data or using a paid model.

## License

Licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.
