# Writing a small app BMI

## Request

- Let's start writing a small app that helps users calculate their BMI and store it as a reference health index.

## Solution

1. Project planning

   - Two pages: home and setting
   - Package: flutter_localizations, intl, dropdown_button2, glassmorphismcard, shared_preferences, provider ...
   - Deploy on Android platform

2. Design app

3. Build and release an Android app

- Create an upload keystore
- Create a file named [project]/android/key.properties that contains a reference to your keystore:

```
storePassword=123456a@
keyPassword=123456a@
keyAlias=upload
storeFile=C:/Users/Admin/upload-keystore.jks
```

- Configure signing in gradle (Read file docs)
- Reviewing the app manifest
- Run flutter build appbundle

4. Upload file release to Google play type internal test
5. Setup CI/CD

- Install Ruby and Bundle
- Create a ./Gemfile in the root directory of your project with the content:

```
source "https://rubygems.org"

gem "fastlane"
```

- Run bundle update
- Run fastlane init
- Set up fastlane (unfinished)

## Conclusion
