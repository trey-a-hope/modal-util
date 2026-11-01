# modal_util

Ready-made toasts, snackbars and dialogs for Flutter apps, so a new project gets consistent success/error feedback and confirmation prompts without writing them again. Confirmation dialogs automatically use Cupertino styling on iOS and macOS and Material everywhere else.

[pub.dev/packages/modal_util](https://pub.dev/packages/modal_util)

## Features

- **Toasts**: `showSuccess`, `showError`, `showInfo` and `showWarning` show colored, auto-closing (3 s) toasts via [`toastification`](https://pub.dev/packages/toastification).
- **Snackbar**: `showSnackbar(context, title)` for a plain `ScaffoldMessenger` message.
- **Yes/No confirmation**: `showConfirmation` returns `true`/`false`, as a `CupertinoAlertDialog` on Apple platforms or an `AlertDialog` elsewhere.
- **Type-to-confirm**: `showInputMatchConfirmation` makes the user type a given string (for example a project name) before a destructive action.
- **Email/password prompt**: `showEmailPasswordDialog` returns an `(email, password)` record, with required-field validation.

## Installation

```yaml
dependencies:
  modal_util: ^25.9.1
```

## Usage

```dart
import 'package:modal_util/modal_util.dart';

ModalUtil.showSuccess(context, title: 'Saved');
ModalUtil.showError(context, title: 'Something went wrong');

final confirmed = await ModalUtil.showConfirmation(
  context,
  title: 'Delete item?',
  message: 'This cannot be undone.',
);

final typed = await ModalUtil.showInputMatchConfirmation(
  context: context,
  title: 'Type the project name to delete it',
  hintText: 'my-project',
  match: 'my-project',
);

final credentials = await ModalUtil.showEmailPasswordDialog(context);
if (credentials != null) {
  final (email, password) = credentials;
}
```

## Project structure

```
lib/
├── modal_util.dart                     # ModalUtil static API
└── widgets/
    ├── email_password_input.dart       # form used by showEmailPasswordDialog
    └── input_match_confirmation.dart   # type-to-confirm dialog body
```

## Development

```sh
flutter pub get
flutter test
```

Requires Dart `^3.8.1`. Dependencies: `toastification`, `gap`, `universal_platform`. See `CHANGELOG.md` for release notes.

## License

The `LICENSE` file currently contains placeholder text, so no license has been chosen yet.
