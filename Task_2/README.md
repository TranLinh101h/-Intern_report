# Use provider to switch language for application

## Request

- Add provider language to switch the app back and forth between English <-> Vietnamese in the repo [ltdangkhoa
/
flutter_demo_todo](https://github.com/ltdangkhoa/flutter_demo_todo.git)

## Solution

- Demo source: [vnappmob
/
qrquick](https://github.com/vnappmob/qrquick.git)

1. Add the intl package to the pubspec.yaml file:

```dart
dependencies:
  flutter:
    sdk: flutter
  flutter_localizations:
    sdk: flutter
  intl: ^0.17.0 # Add this line
```

2. Also, in the pubspec.yaml file, enable the generate flag. This is added to the section of the pubspec that is specific to Flutter, and usually comes later in the pubspec file.

```dart
# The following section is specific to Flutter.
flutter:
  generate: true # Add this line
```

3. Add a new yaml file to the root directory of the Flutter project called l10n.yaml with the following content:

```dart
arb-dir: lib/l10n
template-arb-file: app_en.arb
output-localization-file: app_localizations.dart
```

4. In ${flutter_demo_todo}/lib/l10n, add the app_en.arb template file.

```
{
    "title": "Flutter Demo Home Page",
    "language": "English",
    "titleAdd": "Add new todo",
    "add": "Add"
}
```

5. Next, add an app_es.arb file in the same directory for VietNamese translation of the same message:

```
{
    "title": " Trang Chủ Demo Flutter",
    "language": "Tieng Viet",
    "titleAdd": "Thêm việc làm mới",
    "add": "Thêm"
}
```

6. Run app so that codegen takes place. You should see generated files in ${flutter_demo_todo}/.dart_tool/flutter_gen/gen_l10n.

7. Add the import statement on app_localizations.dart and AppLocalizations.delegate in your call to the constructor for MaterialApp.

```dart
import 'package:flutter_gen/gen_l10n/app_localizations.dart';
```

```dart
return const MaterialApp(
  title: 'Localizations Sample App',
  localizationsDelegates: [
    AppLocalizations.delegate, 
    GlobalMaterialLocalizations.delegate,
    GlobalWidgetsLocalizations.delegate,
    GlobalCupertinoLocalizations.delegate,
  ],
  supportedLocales: AppLocalizations.supportedLocales,
  home: MyHomePage(),
);
```

8. Use AppLocalizations anywhere in your app. Here, the translated message is used in a Text widget.

```dart
 Text(AppLocalizations.of(context)!.titleAdd),
```

9. Use extract widget for MaterialApp widget with name InitApp and use widget Consumer like this:

```dart
class InitApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Consumer<LocaleProvider>(builder: (_, languageModel, child) {
      return MaterialApp(
        title: 'Flutter Demo',
        theme: ThemeData(
          primarySwatch: Colors.blue,
        ),
        locale: languageModel.locale,
        localizationsDelegates: [
          AppLocalizations.delegate,
          GlobalMaterialLocalizations.delegate,
          GlobalWidgetsLocalizations.delegate,
          GlobalCupertinoLocalizations.delegate,
        ],
        supportedLocales: AppLocalizations.supportedLocales,
        home: const MyHomePage(title: 'Flutter Demo Home Page'),
      );
    });
  }
}
```

10. Use extract method for MultiProvider widget with name bootApp() and declare it in main():

```dart
void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await bootApp();
}

Future<void> bootApp() async {
  LocaleProvider languageModel = LocaleProvider();
  await languageModel.fetchLocale();
  runApp(MultiProvider(
    providers: [
      ChangeNotifierProvider(create: (context) => TodoModel()),
      ChangeNotifierProvider(
        create: (context) => languageModel,
      )
    ],
    child: InitApp(),
  ));
}
```

11. Add two button widget in app bar to change language easily:

```dart
 Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            Text(AppLocalizations.of(context)!.title),
            SizedBox(
              width: 55,
              child: FlatButton(
                  color: Colors.green,
                  onPressed: () async {
                    final provider =
                        Provider.of<LocaleProvider>(context, listen: false);
                    await provider.setLocale('en');
                  },
                  child: Text(
                    'EN',
                    style: TextStyle(color: Colors.black, fontSize: 14),
                  )),
            ),
            SizedBox(
              width: 55,
              child: FlatButton(
                color: Colors.yellow,
                onPressed: () async {
                  final provider =
                      Provider.of<LocaleProvider>(context, listen: false);
                  await provider.setLocale('vi');
                },
                child: Text(
                  "VI",
                  style: TextStyle(color: Colors.black, fontSize: 14),
                ),
              ),
            )
          ],
        ),
```

## Conclusion

After completing this task I learned:
- How to manage simple application state with Provider package.
- How to use multi language in app.
