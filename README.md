# Base Flutter Project
This project is a starting point for a Flutter application.

## Prerequisites (friend setup)
- Flutter SDK `>=3.12.0 <4.0.0` (pinned `3.44.7` in `.fvmrc`; easiest is
  [FVM](https://fvm.app): `fvm install && fvm flutter pub get`).
- Android SDK for APK builds / Android Studio or VS Code with Flutter ext.
- `flutter pub get` before the first run (generated `.g.dart`/`.freezed.dart`
  files are committed, no `build_runner` needed).

## Getting Started

# the last changes in Base
- allow multi flavors in one project to determine app name,logo and app id
- add obs value and obs value consumer to build widget when value changed without using state
- add base bloc for build widget using states
- add Requester and Requester Consumer to handle Get Requests with status and error handling
- replace Either with Result
- add shimmer widgets
- add base option field to replace dropdown field
- add app bottom sheets
- add app buttons
- add app text spans
- Translation auto generate

# Notes for Developers
- Widgets should be stateless as possible and start with noun and end with keyword widget
- use requester instead of use case
- create domain models if needed only
- use factory constructors when needed
- use when in multi conditions
- please separate  package in helper and make it easy to be replaced when needed
- use isNullEmptyOrWhitespace to check if string is null or empty or whitespace
- use isNullOrEmpty to check if list is null or empty
- use SvgIconWrapper to call svg icons
- use AppSnackBar to show snack bar or toast
- use file service to handle files
- use permission service to handle permissions
- use share service to share data like (open link, call number, send email, share text, share file)
- use AppLoaderWidget to show loader using it's factory constructor


# Localizations
- to generate localizations run this command "dart run intl_utils:generate"

# To Build Release Version
- dart run lib/env/env_specific_handlers/dev_handler.dart
- flutter build apk --release --no-tree-shake-icons --dart-define-from-file=.run/json/dev.json  --flavor dev

# Run against the hosted backend (for testers)
- The backend runs on a host machine and is exposed over a tunnel URL.
- The current tunnel URL lives in `.run/json/host.json` (`APP_BASE_URL`).
  If the host restarts, that URL changes — ask the host for the fresh one and
  update `APP_BASE_URL` (keep the trailing `/`).
- flutter run --dart-define-from-file=.run/json/host.json
- flutter build apk --debug --dart-define-from-file=.run/json/host.json
- Sign up inside the app (new accounts are Traveler). The app sends
  `X-Dahab-Client: native` and receives the session token in the login
  response body, then uses it as `Authorization: Bearer`.