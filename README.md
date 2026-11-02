Sc Chat — Android 0.9.0

<p align="center">Android · Minimal Workspace · Multi-Provider · Sc Reasoning Engine</p>Sc Chat is a lightweight Android AI workspace by Sc Ai Lab. It keeps a clean chat-first interface while organizing conversations, projects, assistants, model connections, and local files in one place.

What's new in 0.9.0

- Added composer-based Thinking Mode and Reasoning Amount controls. Preferences are stored per local account.
- Added three modes: Off, Native Reasoning, and Sc Reasoning Engine.
- Native mode sends "reasoning_effort" as "low", "medium", or "high" only when the selected model is explicitly registered as supporting that parameter. If a provider rejects the parameter, Sc Chat automatically falls back to Sc Reasoning Engine.
- Sc Reasoning Engine provides a prompt-orchestrated multi-stage path for ordinary OpenAI-compatible chat-completion APIs:
  - Light: task map → final answer (2 API calls)
  - Standard: task map → provisional answer → final answer (3 API calls)
  - Deep: task map → provisional answer → independent review → final answer (4 API calls)
- Multi-stage input and output estimates, plus API call counts, are included in local usage tracking.
- Added estimated token-consumption ranges in the composer, relative to a normal single-pass request.

Understanding Sc Reasoning Engine

Sc Reasoning Engine is an orchestration layer, not a local model and not true token-level decoder control. It can work with remote models that do not expose native reasoning parameters by running multiple structured API calls and passing compact task notes between stages. It cannot suppress EOS or reasoning-end tokens, inject tokens into a remote model's live decoding loop, or guarantee better answers merely by spending more tokens.

A real adaptive decoder controller requires control over the model's generation loop, such as a local inference runtime or a server that exposes token-level decoding hooks. That capability is not claimed by this release.

Token-use estimates

The composer shows rough ranges relative to an ordinary single-pass request:

Mode| Light| Standard| Deep
Off| 1.0×| 1.0×| 1.0×
Native Reasoning| 1.2–2×| 1.5–3×| 2–4×
Sc Reasoning Engine| 2–3×| 3–4×| 4–6×

These are planning estimates, not provider guarantees. Actual usage depends on model behavior, conversation length, generated answer length, hidden reasoning tokens, image/file inputs, caching, and provider billing rules. Sc Engine resends conversation context in multiple stages, so long conversations and large attachments can increase usage substantially. Image tokens are not included in the app's text-based local estimate. Native reasoning usage may include hidden tokens that a generic API does not report. Always use the provider's own usage and billing records as the source of truth.

Existing features

- Local device accounts and profiles
- Chat history, projects, and custom assistants
- Multi-provider connections and model selection
- Pollinations device authorization with lifecycle recovery
- Android Keystore-protected provider credentials
- Images, text files, and text-based PDF attachments
- Local file library, conversation export, and usage estimates
- Light and dark system appearance

Build from GitHub Actions

1. Upload "ScChat_0.9.0_ReasoningEngine.zip" to the root of your private GitHub repository.
2. Copy "build-from-zip-0.9.0.yml" to ".github/workflows/build-from-zip.yml".
3. Open Actions and run Build Sc Chat 0.9.0 APK.
4. Download the "ScChat-0.9.0-debug" artifact.

The workflow runs JavaScript regression tests, Android XML validation, Gradle assembly, package/version checks, and APK signature verification.

Compatibility

- Application ID: "ai.scailab.chat"
- Version code: "14"
- Version name: "0.9.0"
- Minimum Android version: Android 8.0 (API 26)
- Compile / target SDK: 35
- Existing local storage namespace, application ID, and development signing configuration are retained for update compatibility. Keep the project in a private repository; do not publish the development keystore.

Privacy and limitations

Local account and chat data are stored on the device. Provider API credentials and Pollinations authorization secrets are encrypted using Android Keystore. Chat content and attachments in local storage are not end-to-end encrypted. API requests, including Sc Engine's intermediate stage requests, are sent to the selected provider. Review that provider's privacy policy and redact sensitive information before sending files.

Provider usage and cost figures are local estimates, not official billing data. Scanned PDFs requiring OCR are not supported. The operating system may still reclaim background processes; the app is designed to restore saved state when it is recreated.

License

Apache-2.0.