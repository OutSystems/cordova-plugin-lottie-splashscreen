# Contributing to cordova-plugin-lottie-splashscreen

Thank you for your interest in contributing to this Cordova plugin for Lottie splash screens.

## Development Setup

### Prerequisites

- **Node.js**: Version specified in `.node-version`
- **npm**: For dependency management
- **iOS Development** (for iOS platform work):
  - macOS with Xcode
  - CocoaPods: `sudo gem install cocoapods && pod setup`
  - Swift 5.5+ (specified in Cordova config.xml)
- **Android Development** (for Android platform work):
  - Android Studio
  - Kotlin support (enabled by default in cordova-android >= 9.0.0)
  - AndroidX support

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/OutSystems/cordova-plugin-lottie-splashscreen.git
cd cordova-plugin-lottie-splashscreen
npm install
```

The `prepare` script will automatically set up Husky git hooks for commit linting and pre-commit formatting.

## Development Workflow

### Branch Naming

No strict branch naming convention is enforced. Recent branches show various patterns including:
- Feature branches: `parent-repo-sync`
- Dependency updates: `dependabot/npm_and_yarn/...`
- Security fixes: `snyk-fix-...`

### Commit Messages

This project uses **Conventional Commits** format enforced by commitlint with the Angular preset.

**Format**: `<type>(<scope>): <subject>`

**Allowed types**:
- `feat`: New features
- `fix`: Bug fixes
- `perf`: Performance improvements
- `refactor`: Code refactoring
- `revert`: Reverts a previous commit
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `test`: Adding or updating tests
- `build`: Changes to build system
- `ci`: CI configuration changes
- `chore`: Other changes that don't modify src or test files

**Examples**:
```
feat(android): add support for hardware acceleration
fix(ios): resolve color parsing issue for dark mode
docs: update installation instructions
```

The commit message hook will automatically validate your commits before they are created.

## Building and Testing

### Build Commands

| Command | Description |
|---------|-------------|
| `npm run build` | Compile TypeScript files to JavaScript |
| `npm run lint` | Run all linters (Android, iOS, TypeScript) |
| `npm run lint:android` | Lint Kotlin files with ktlint |
| `npm run lint:ios` | Lint Swift files with SwiftLint |
| `npm run lint:typescript` | Lint TypeScript files with ESLint |

### Pre-publish Process

TypeScript is automatically compiled before publishing via the `prepublishOnly` script.

## Code Standards

### TypeScript

- **Linter**: ESLint with TypeScript strict type checking
- **Formatter**: Prettier
- **Configuration**: See `eslint.config.mjs` and `.prettierrc`
- **Style**:
  - Single quotes preferred
  - Print width: 140 characters
  - Unused variables starting with `_` are allowed
  - Strict null checks and type safety required

### Kotlin (Android)

- **Linter**: ktlint
- **Configuration**: See `.editorconfig`
- **Style**:
  - 4-space indentation
  - Import ordering check is disabled
  - Files located in `src/android/`

### Swift (iOS)

- **Linter**: SwiftLint
- **Configuration**: See `.swiftlint.yml`
- **Style**:
  - Line length: 140 characters
  - Only files in `src/ios/` are linted

### General Formatting

- **EditorConfig**: Enforces consistent coding styles (see `.editorconfig`)
  - Unix-style line endings (LF)
  - Final newline required
  - Trailing whitespace trimmed (except in markdown)
  - 4-space indentation for most files, 2 spaces for YAML and package.json

### Pre-commit Hooks

Husky and lint-staged automatically format staged files before commit:
- TypeScript, JSON, CSS, Markdown, and YAML files are formatted with Prettier

## Pull Request Process

1. **Create a feature branch** from `main`
2. **Make your changes** following the code standards above
3. **Write or update tests** if applicable
4. **Run linters** with `npm run lint` to ensure code quality
5. **Build the project** with `npm run build` to verify TypeScript compilation
6. **Commit your changes** using conventional commit format
7. **Push your branch** and create a pull request against `main`
8. **Address review feedback** if requested

### PR Description

Include in your PR description:
- Summary of changes
- Motivation for the changes
- Testing performed (devices, OS versions tested)
- Screenshots or videos if UI-related
- Any breaking changes or migration notes

## Versioning

This project uses `standard-version` for automated versioning and changelog generation based on conventional commits.

**Release Process** (for maintainers):
```bash
npm run release
```

This will:
- Bump version in `package.json` based on commit types
- Update `plugin.xml` version via post-bump script
- Generate/update `CHANGELOG.md`
- Create a git tag

## Testing Your Changes

### Manual Testing

Use the example project in the `example/` directory to test plugin changes:

```bash
cd example
cordova platform add android
cordova platform add ios
cordova run android
cordova run ios
```

### Platform-Specific Requirements

- **iOS**: Requires cordova-ios >= 5.0.0 and iOS >= 11.0
- **Android**: Requires cordova-android >= 9.0.0

For common issues and troubleshooting, refer to [FAQ.md](FAQ.md).

## Additional Resources

- **Issue Templates**: Use the provided templates in `.github/ISSUE_TEMPLATE/` for bug reports and feature requests
- **Version Information**: When reporting issues, include output of `cordova info` (not `ionic info`)
- **Example Project**: See `example/` directory for a complete working implementation

## Questions?

If you have questions about contributing, please open an issue with your question.
