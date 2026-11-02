
# Sc Chat — Android 0.7.2

<p align="center">
  <img src="app/src/main/assets/logo.png" width="112" alt="Sc Ai Lab Atom Logo">
</p>

<p align="center">
  <strong>Your AI Workspace by Sc Ai Lab</strong>
</p>

<p align="center">
  Android · Multi-Provider · Local-First · 0.7.2
</p>

---

## Overview

Sc Chat is an Android AI workspace developed by Sc Ai Lab.

It provides a unified interface for AI conversations, projects, custom assistants, model providers, and local file management.

The application features an independent blue visual identity, an atom-inspired logo, automatic system light/dark themes, and a mobile-first interface.

## What's New in 0.7.2

This release focuses on input focus isolation and Android application lifecycle stability.

### Input Focus Improvements

- Prevents account profile fields from triggering the main chat composer layout.
- Separates keyboard state from the active input field.
- Adds global focus tracking.
- Rechecks the active input after delayed keyboard callbacks.
- Clears chat composer focus when opening account dialogs.
- Preserves normal keyboard behavior in profile editing dialogs.

### Android Lifecycle Improvements

- Adds WebView pause and resume handling.
- Saves WebView state through Android Activity lifecycle callbacks.
- Restores WebView state when possible.
- Handles WebView renderer process termination.
- Defers renderer recovery until the application returns to the foreground.
- Saves and restores the last workspace location.
- Preserves the selected conversation, project, provider, and assistant where possible.

**Important:** Android may terminate background processes under memory pressure. Sc Chat cannot prevent all system process termination, but it attempts to restore the previous workspace when reopened.

## Features

### 1. Chat Workspace

- Create and manage conversations.
- Streaming assistant responses.
- Stop response generation.
- Copy assistant messages.
- Edit previous user messages.
- Regenerate assistant responses.
- Markdown rendering.
- Code block formatting and copy actions.
- Image and document attachments.
- Android keyboard-aware message composer.

### 2. Projects

- Create, edit, and delete projects.
- Organize related conversations.
- Create conversations inside projects.
- Move conversations between projects.
- View project-related conversation history.

Deleting a project does not automatically delete its conversations.

### 3. Custom AI Assistants

- Create custom assistants.
- Edit assistant names and instructions.
- Configure assistant-specific system prompts.
- Select assistants for conversations.
- Manage local assistant configurations.

### 4. Models & Connections

- Pollinations integration.
- OpenAI-compatible API providers.
- Custom API base URLs.
- Custom model IDs.
- Provider-specific API keys.
- Model selection.
- Per-model Vision capability configuration.
- Per-model Streaming configuration.
- Context window configuration.
- Input and output pricing configuration.
- Provider connection testing.
- Model discovery through compatible model-list endpoints.

### 5. Usage & Budget

- Local request statistics.
- Estimated input and output tokens.
- Estimated model usage costs.
- Monthly budget configuration.
- Budget warning thresholds.

Usage and cost figures are estimates, not official provider billing records.

### 6. File Library

- Collect attachments from saved conversations.
- Browse images and documents.
- Search files by filename or conversation title.
- Navigate back to the original conversation.
- Support text extraction from text-based PDF documents.

Scanned image-only PDFs may not support text extraction.

### 7. Local Accounts

- Local registration and login.
- Profile display-name editing.
- Profile image editing.
- Password changes.
- Local account deletion.

The account system is device-local. It does not currently support cloud synchronization or password recovery.

### 8. Appearance

- Automatic Android system light/dark theme.
- Blue accent color.
- Sc Ai Lab atom emblem.
- Mobile-responsive layout.
- Android status bar and navigation bar inset handling.

## Navigation Structure

| Section | Description |
|---|---|
| Conversations | Chat history and new conversations |
| Projects | Organize related conversations |
| AI Assistants | Manage custom AI assistants |
| Models & Connections | Configure AI providers |
| File Library | Browse conversation attachments |
| Account & Settings | Manage local profile and preferences |

## System Requirements

- Android 8.0 (API 26) or later.
- Internet connection for remote AI providers.
- Valid API credentials where required.
- HTTPS API endpoint for custom OpenAI-compatible providers.

## Installation Using GitHub Actions

1. Upload `ScChat_0.7.2_LifecycleFix.zip` to the repository root.
2. Place the workflow YAML at `.github/workflows/build-from-zip.yml`.
3. Open the GitHub Actions tab.
4. Run **Build Sc Chat 0.7.2 APK**.
5. Wait for the build and verification steps.
6. Download the `ScChat-0.7.2-debug` artifact.
7. Extract and install `app-debug.apk` on Android.

The generated APK is a debug build intended for testing.

## Build from Source

### Requirements

- JDK 17.
- Android SDK Platform 35.
- Android Build Tools 35.0.0.
- Gradle 8.9.

### Build Command

```bash
gradle --no-daemon :app:assembleDebug
```

Generated APK:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## Custom Provider Configuration

Open:

**Models & Connections → Add OpenAI-Compatible Provider**

Configure:

```text
Provider Name: My Provider
Base URL: https://api.example.com/v1
Model ID: example-model
API Key: your-api-key
```

These are illustrative values, not actual service credentials.

Always verify provider compatibility, pricing, rate limits, and data handling policies.

## Privacy & Local Data

Sc Chat follows a local-first design.

- Conversations are stored locally.
- Projects and assistants are stored locally.
- Profile information is stored locally.
- File Library entries are derived from local conversation attachments.
- Provider credentials are handled through the Android Keystore integration.
- Prompts and attachments are transmitted to the selected provider when submitted.

Avoid entering passwords, private credentials, or unnecessary sensitive information into AI conversations.

## Compatibility & Upgrade Notes

| Configuration | Value |
|---|---|
| Android Application ID | `ai.scailab.chat` |
| Internal storage namespace | `scailab.*` |
| Version Code | `11` |
| Version Name | `0.7.2` |
| Minimum Android Version | Android 8.0 |

Keeping the Application ID and storage namespace unchanged helps preserve compatibility with previous installations.

For an in-place upgrade, the APK must use the same signing certificate as the installed version.

Back up important local data before uninstalling an existing version.

## Roadmap

- [x] Local accounts
- [x] Profile settings
- [x] Streaming conversations
- [x] Multiple AI providers
- [x] Custom AI assistants
- [x] Project management
- [x] Local file library
- [x] System light/dark theme
- [x] Keyboard layout improvements
- [x] Provider management
- [x] Usage and budget estimates
- [x] Account input focus isolation
- [x] WebView lifecycle handling
- [x] Workspace state restoration
- [ ] Long-term conversation memory
- [ ] Advanced context management
- [ ] Knowledge collections
- [ ] Retrieval-Augmented Generation (RAG)
- [ ] Voice input and speech output
- [ ] Local model inference
- [ ] Native HSSM integration
- [ ] Encrypted conversation database
- [ ] Local data backup and restoration

## Development Direction

Sc Chat is designed as a unified AI workspace.

Its long-term architecture focuses on three areas:

**Chat**

A flexible conversation interface for different AI models.

**Projects**

A workspace for long-running tasks, documents, and contextual information.

**Models**

A unified connection layer for third-party cloud models, local inference engines, and Sc Ai Lab's own HSSM models.

The long-term goal is to integrate HSSM as a native model option.

## About Sc Ai Lab

Sc Ai Lab is an independent AI development project focused on model architecture, long-context systems, AI applications, and safety alignment.

Sc Chat is part of the Sc Ai Lab software ecosystem.

## License

Licensed under the Apache License 2.0.

See the `LICENSE` file for details.

## Disclaimer

Sc Chat 0.7.2 is an experimental development release.

Some features may have limitations. Actual compatibility depends on the Android device, selected AI provider, and network conditions.

Always verify provider pricing and privacy policies before use.
