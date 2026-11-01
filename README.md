
# Sc Ai Lab Chat

<p align="center">
  <strong>A lightweight, extensible AI chat client for Android.</strong>
</p>

<p align="center">
  Version 0.4.0 · Android · Java · WebView
</p>

---

## Overview

Sc Ai Lab Chat is an Android AI chat application developed by Sc Ai Lab.

It aims to provide a clean, accessible, and extensible interface for interacting with different AI models and service providers.

The application is designed around provider independence, allowing users to configure compatible AI services instead of relying on a single model provider.

## Features

### Chat Experience
- Real-time streaming responses.
- Stop generation at any time.
- Copy AI responses.
- Edit previous user messages.
- Regenerate AI responses.
- Markdown rendering.
- Code blocks and syntax highlighting.
- Table rendering.

### Provider Management
- Pollinations integration.
- Custom OpenAI-compatible API providers.
- Configurable API Base URL.
- Configurable model identifiers.
- Provider switching.
- API key encryption using Android Keystore.

### Conversation Management
- Create and manage multiple conversations.
- Search conversation history.
- Rename conversations.
- Pin important conversations.
- Delete conversations.
- Export individual conversations as Markdown.
- Export conversation backups as JSON.

### Interface
- Clean and minimal interface.
- Blue accent color.
- Automatic light and dark theme support.
- Android system-bar compatibility.
- Responsive mobile layout.

### Local Account System
- Local registration and login.
- Password hashing.
- Local conversation storage.

**Note:** Local accounts are device-specific and do not support cloud synchronization.

## Technology Stack

| Component | Technology |
|---|---|
| Android application | Java |
| User interface | HTML, CSS, JavaScript |
| Android container | WebView |
| Android integration | AndroidX WebKit |
| Build system | Gradle |
| AI communication | HTTPS APIs |
| API key protection | Android Keystore |
| Markdown rendering | Client-side renderer |
| CI/CD | GitHub Actions |

## Requirements

- Android 8.0 (API 26) or later.
- Internet connection.
- An API key for providers that require authentication.
- Compatible AI service endpoint.

## Installation

### Option 1: Download a Debug APK

1. Open the repository's GitHub Actions page.
2. Select a successful build.
3. Find the Artifacts section.
4. Download `ScAiLabChat-0.4.0-debug`.
5. Extract the downloaded artifact if necessary.
6. Install `app-debug.apk` on your Android device.

### Option 2: Build from Source

Requirements:

- Android SDK 35.
- JDK 17.
- Gradle 8.9.

Build command:

```bash
gradle --no-daemon :app:assembleDebug
```

The generated APK will be located at:

```text
app/build/outputs/apk/debug/app-debug.apk
```

## Configure an AI Provider

Open:

**Settings → Provider Management → Add Provider**

Enter the following information:

| Field | Description |
|---|---|
| Provider Name | A display name for the provider |
| Base URL | HTTPS API endpoint |
| Model ID | Model identifier |
| API Key | Provider authentication key |

Example configuration:

```text
Provider Name: My AI Provider
Base URL: https://api.example.com/v1
Model ID: your-model-name
API Key: your-api-key
```

The example endpoint is illustrative and is not a working service.

### API Key Security

Custom provider credentials are encrypted on Android using Android Keystore-backed encryption.

Users should avoid sharing API keys or including them in screenshots, logs, or exported project files.

Provider pricing and usage limits are determined by the respective service providers.

## Project Structure

```text
ScAiLabChat/
├── app/
│   ├── src/
│   │   └── main/
│   │       ├── java/
│   │       │   └── ai/scailab/chat/
│   │       │       └── MainActivity.java
│   │       ├── assets/
│   │       │   ├── index.html
│   │       │   ├── app.js
│   │       │   ├── styles.css
│   │       │   └── logo.png
│   │       ├── res/
│   │       └── AndroidManifest.xml
│   └── build.gradle.kts
├── gradle/
├── settings.gradle.kts
└── build.gradle.kts
```

## Privacy and Data Storage

- Local accounts and conversations are stored on the device.
- Custom provider API keys are encrypted using Android Keystore.
- AI requests are sent to the provider selected by the user.
- Each provider may process requests according to its own privacy policy.
- Users should not submit sensitive personal information to untrusted AI services.

Sc Ai Lab does not guarantee the privacy practices of third-party AI providers.

## Roadmap

### Completed in 0.4.0

- [x] Streaming responses
- [x] Stop generation
- [x] Message actions
- [x] Markdown rendering
- [x] Custom provider architecture
- [x] Conversation management
- [x] Markdown and JSON export
- [x] Encrypted provider credentials

### Planned

- [ ] File uploads
- [ ] PDF document analysis
- [ ] Image understanding
- [ ] Custom AI assistants
- [ ] Advanced context management
- [ ] Improved local data encryption
- [ ] HSSM model integration
- [ ] Cloud synchronization

## About Sc Ai Lab

Sc Ai Lab is an independent AI development project focused on model architecture, AI applications, and accessible AI technologies.

Sc Ai Lab Chat is part of the broader Sc Ai Lab ecosystem.

Our long-term goal is to build an extensible AI application platform that can integrate both third-party models and our own HSSM models.

## Disclaimer

This project is under active development.

The current version is intended for testing and development purposes. Features, compatibility, and API integrations may change between releases.

Third-party AI providers are independent services. Sc Ai Lab is not responsible for their pricing, availability, or service policies.

## License

Licensed under the Apache License 2.0.

See the [LICENSE](LICENSE) file for details.
# sc-ai-lab-chat-test