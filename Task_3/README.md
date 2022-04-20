# Create a package and publish to pub.dev

## Request

- In our Flutter projects, we often use Card style to wrap content. You could take a look at the card style at our app Setting page. A single card might have header (with left, center, right item) in differ with body (can wrap a child content) by deeper color...
- We are asking you to build this card to a package and publish to pub.dev
- Extra: nowadays, the Glassmorphism becoming trend in UI/UX. Could you make that card to have glassmorphism style?

## Solution

1. Create a pakage

- Create a package using Visual studio or in the terminal:

```
flutter create --template=package glassmorphismcard
```

2. Create a new stateful widget and define the properties

```dart
class GlassmorphismCard extends StatefulWidget {
  final double width;
  final double height;
  final Color color_Header;
  final Color color_Body;
  final Widget? leading;
  final Widget? title;
  final Widget? trailing;
  final Widget? body;

```
3. Define constructor

```dart
 GlassmorphismCard(
      {this.width = 350,
      this.height = 150,
      this.color_Header = Colors.white,
      this.color_Body = Colors.cyan,
      this.leading,
      this.title,
      this.trailing,
      this.body});

  @override
  GlassmorphismCardState createState() => GlassmorphismCardState();
}
```

4. Let's design a card in class GlassmorphismCardState

```dart
class GlassmorphismCardState extends State<GlassmorphismCard> {
  @override
  Widget build(BuildContext context) {
    return Container(
      height: widget.height,
      width: widget.width,
      child: Card(
          color: widget.color_Header.withOpacity(0.5),
          child: Column(
            children: [
              Container(
                child: Stack(
                  children: [
                    Align(
                      alignment: Alignment.topLeft,
                      child: Padding(
                        padding: const EdgeInsets.all(8.0),
                        child: widget.leading,
                      ),
                    ),
                    Align(
                      alignment: Alignment.topCenter,
                      child: Padding(
                        padding: const EdgeInsets.all(8.0),
                        child: widget.title,
                      ),
                    ),
                    Align(
                      alignment: Alignment.topRight,
                      child: Padding(
                        padding: const EdgeInsets.all(8.0),
                        child: widget.trailing,
                      ),
                    ),
                  ],
                ),
              ),
              Expanded(
                  child: Align(
                alignment: Alignment.center,
                child: Container(
                  width: widget.width,
                  height: widget.height - 50,
                  padding: EdgeInsets.symmetric(horizontal: 10, vertical: 10),
                  color: widget.color_Body.withOpacity(0.7),
                  child: widget.body,
                ),
              )),
            ],
          )),
    );
  }
}
```

5. Ready to publish

- Go over to pubspec.yaml and check the name, the description and the version of the package. Create new repo and past the link in homepage:

```
name: glassmorphismcard
description: create a card have glassmorphism style.
version: 0.0.1
homepage: https://github.com/TranLinh101h/glassmorphism_card.git
```

- Modify the CHANGELOG.md and describe what all features is available in the version.

- Write the README.md

6. Type 'flutter pub publish --dry-run' in the terminal to check for any warnings

7. Type 'flutter pub publish' in the terminal to publish the package.

## Conclusion

After completing this task I learned how to make a Flutter Package and publish it to pub.dev.
