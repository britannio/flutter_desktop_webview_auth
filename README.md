# Desktop webview auth

This package enables Firebase OAuth on desktop via webview

## Supported providers:

- Google
- Facebook
- Twitter

## Installation

Add dependency

```bash
flutter pub add desktop_webview_auth
```

Imports

```dart
import 'package:desktop_webview_auth/desktop_webview_auth.dart';
import 'package:desktop_webview_auth/google.dart';
import 'package:desktop_webview_auth/facebook.dart';
import 'package:desktop_webview_auth/twitter.dart';
```

## Usage

- Configure OAuth providers in firebase console
- Create an instance of `ProviderArgs`

```dart
final googleSignInArgs = GoogleSignInArgs(
  clientId:
    '448618578101-sg12d2qin42cpr00f8b0gehs5s7inm0v.apps.googleusercontent.com',
  redirectUri:
    'https://react-native-firebase-testing.firebaseapp.com/__/auth/handler',
)
```

- call `DesktopWebviewAuth.signIn`

```dart
try {
    final result = await DesktopWebviewAuth.signIn(args);

    print(result?.accessToken);
    print(result?.tokenSecret);
} catch (err) {
    // something went wrong
}
```

- create an instance of `OAuthCredential` and sign in

```dart
import 'package:firebase_auth/firebase_auth.dart';

final credential = GoogleAuthProvider.credential(accessToken: result.accessToken)

FirebaseAuth.instance.signInWithCredential(credential);
```
