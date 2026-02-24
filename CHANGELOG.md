# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-24

### Added

- Initial release of Skill Issue extension
- Renamed from "Faah on Fail" to "Skill Issue"
- Added extension icon
- Added MIT License
- Added repository, bugs, and homepage fields to package.json

## [0.1.0] - 2026-02-23

### Phase 6: Polish & UX

- Enhanced status bar item with proper icons and tooltips
- Added first-install notification with "Test Sound" and "Settings" buttons
- Added graceful error handling (missing audio file, playback failures)
- Added comprehensive output channel logging

### Phase 5: Extension Settings (Configuration)

- Added 7 configurable settings in package.json:
  - `skillIssue.enabled` - Enable/disable the extension
  - `skillIssue.volume` - Audio playback volume
  - `skillIssue.cooldownMs` - Cooldown period between sounds
  - `skillIssue.customAudioPath` - Path to custom audio file
  - `skillIssue.useTestExplorerApi` - Enable Test Explorer API detection
  - `skillIssue.useTerminalDetection` - Enable terminal output detection
  - `skillIssue.showStatusBarMessage` - Show status bar messages
- Created Config interface and getConfig() function with validation

### Phase 4: Wire Everything Together

- Connected detection modules to audio player
- Created failure handler with status bar message
- Registered commands:
  - `skill-issue.toggle` - Toggle extension on/off
  - `skill-issue.playTest` - Play test sound manually
  - `skill-issue.selectSound` - Select custom sound file
- Created status bar item with click to toggle
- Added configuration change listener

### Phase 3: Test Failure Detection - Terminal Output Fallback

- Implemented registerTerminalListener() with multiple strategies:
  - Task-based detection (onDidEndTaskProcess)
  - Shell Integration API (onDidEndTerminalShellExecution)
  - Terminal exit code detection (onDidCloseTerminal)
- Added 1-second debouncing
- Configurable enable/disable via settings

### Phase 2: Test Failure Detection - VS Code Test API

- Implemented registerTestResultListener() using vscode.tests.onDidChangeTestResults
- Handles TestResultState.Failed and TestResultState.Errored
- Duplicate prevention with Set<string> keyed on testRunId:testItemId
- Graceful degradation on older VS Code versions

### Phase 1: Audio Playback Engine

- Created AudioPlayer class with cross-platform support:
  - macOS: afplay
  - Linux: ffplay
  - Windows: PowerShell
- Added cooldown mechanism (2 seconds default)
- Created VS Code OutputChannel for debug logging
- Created createAudioPlayer() singleton factory function

### Phase 0: Project Scaffolding

- Created VS Code extension skeleton
- Set up folder structure (src/, src/audio/, src/testWatcher/, media/)
- Created package.json, tsconfig.json, esbuild.js, .vscodeignore
- Installed dependencies
- Created minimal extension.ts with activate/deactivate

## [0.0.1] - 2026-02-23

### Added

- Initial release
- Project scaffolding
