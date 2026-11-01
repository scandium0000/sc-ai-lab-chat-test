
# Sc Chat — Android 0.6.1

<p align="center">
  <img src="app/src/main/assets/logo.png" width="112" alt="Sc Ai Lab Atom Logo">
</p>

<p align="center">
  <strong>Your AI Workspace by Sc Ai Lab</strong>
</p>

<p align="center">
  Android · Multi-Provider · Local-First · 0.6.1
</p>

---

## Overview

**Sc Chat** is an Android AI chat application developed by **Sc Ai Lab**.

It provides a unified mobile workspace for AI conversations, projects, custom assistants, model connections, and local file management.

Sc Chat features an independent blue visual identity, an atom-inspired application icon, automatic system light/dark themes, and a mobile-first interface.

The project aims to support multiple AI providers rather than depending on a single model service.

## What's New in 0.6.1

This release focuses on Android keyboard handling and interface stability.

### Keyboard & Input Improvements

- Improved Android IME (soft keyboard) handling.
- Native Android WindowInsets integration.
- Dynamically adjusts the WebView's available layout area when the keyboard appears.
- Keeps the message composer above the keyboard.
- Prevents unnecessary whole-page scrolling when focusing the input field.
- Preserves `adjustResize` compatibility for older Android versions.

### System UI Improvements

- Improved status bar and navigation bar inset handling.
- Better separation between the top toolbar and Android status bar.
- Improved system bar icon appearance in light and dark themes.
- Reduced layout conflicts with Android edge-to-edge display behavior.

### Regression Checks

- JavaScript syntax validation.
- HTML control reference checks.
- CSS and Android XML validation.
- YAML and shell syntax validation.
- Simulated viewport regression tests at multiple heights.

**Note:** These checks do not replace a real Android device test. The final keyboard behavior must be verified on an actual device.

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
- Mobile keyboard-aware message composer.

### 2. Projects

- Create, edit, and delete projects.
- Organize related conversations.
- Create conversations inside projects.
- Move existing conversations between projects.
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
- Vision capability configuration.

Provider pricing, availability, quotas, and privacy policies are determined by the respective provider.

### 5. File Library

- Collect attachments from saved conversations.
- Browse images and documents.
- Search files by filename or conversation title.
- Navigate back to the original conversation.
- Support text extraction from text-based PDF documents.

Scanned image-only PDFs are not guaranteed to support text extraction.

### 6. Local Accounts

- Local registration and login.
- Profile display-name editing.
- Profile image editing.
- Password changes.
- Local account deletion.

The account system is device-local. It does not currently support cloud synchronization or password recovery.

### 7. Appearance

- Automatic Android system light/dark theme.
- Blue accent color.
- Sc Ai Lab atom emblem.
- Mobile-responsive layout.
- Improved Android status bar integration.

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
- A valid API credential for providers that require authentication.
- HTTPS API endpoint for custom OpenAI-compatible providers.

## Installation

### Build Using GitHub Actions

1. Upload `ScChat_0.6.1_KeyboardFix.zip` to the repository root.
2. Place the workflow YAML at `.github/workflows/build-from-zip.yml`.
3. Open the GitHub Actions tab.
4. Run **Build Sc Chat 0.6.1 APK**.
5. Wait for the build and verification steps to finish.
6. Download the `ScChat-0.6.1-debug` artifact.
7. Extract the artifact and install `app-debug.apk` on Android.

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

The generated APK should be located at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## Custom Provider Configuration

Open:

**Models & Connections → Add OpenAI-Compatible Provider**

Configure the following fields:

```text
Provider Name: My Provider
Base URL: https://api.example.com/v1
Model ID: example-model
API Key: your-api-key
```

These are illustrative configuration values, not actual service credentials.

Always verify the provider's API compatibility, pricing, rate limits, and data handling policies.

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

The following identifiers remain unchanged:

| Configuration | Value |
|---|---|
| Android Application ID | `ai.scailab.chat` |
| Internal storage namespace | `scailab.*` |
| Version Code | `8` |
| Version Name | `0.6.1` |
| Minimum Android Version | Android 8.0 |

Keeping the Application ID and storage namespace unchanged helps preserve compatibility with previous installations.

For an in-place upgrade, the APK must be signed with the same signing certificate as the installed version.

If Android reports a signature conflict, do not uninstall the old version before backing up important local data.

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
- [x] Android system inset handling
- [ ] Long-term conversation memory
- [ ] Context management
- [ ] Knowledge collections
- [ ] Retrieval-Augmented Generation (RAG)
- [ ] Voice input and speech output
- [ ] Local model inference
- [ ] Native HSSM integration
- [ ] Encrypted conversation database
- [ ] Local data backup and restoration

## Development Direction

Sc Chat is intended to become a unified AI workspace.

Its long-term architecture will focus on three areas:

**Chat**

A flexible conversation interface for different AI models.

**Projects**

A workspace for long-running tasks, documents, and contextual information.

**Models**

A unified connection layer for third-party cloud models, local inference engines, and Sc Ai Lab's own HSSM models.

The long-term goal is to integrate HSSM as a native model option without sacrificing compatibility with external providers.

## About Sc Ai Lab

Sc Ai Lab is an independent AI development project focused on model architecture, long-context systems, AI applications, and safety alignment.

Sc Chat is part of the Sc Ai Lab software ecosystem.

## License

This project is licensed under the Apache License 2.0.

See the `LICENSE` file for details.

## Disclaimer

Sc Chat 0.6.1 is an experimental development release.

Some features may change or have limitations. Actual compatibility depends on the Android device, selected AI provider, and available network services.

Always verify API pricing and provider policies before use.
