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
class GlassmorphismCard extends StatelessWidget {
  final double width;
  final double height;
  final Color backgroundColor;
  final Color? titleColor;
  final Color borderColor;
  final double borderSize;
  final Widget title;
  final Widget? body;
  final Alignment alignTitle;
  final double opacity;
  final double circular;

```
3. Define constructor

```dart
GlassmorphismCard(
      {this.width = 300,
      this.height = 250,
      this.opacity = 0.4,
      this.circular = 20,
      this.backgroundColor = Colors.white,
      this.borderColor = Colors.white,
      this.borderSize = 1,
      this.titleColor,
      required this.title,
      this.body,
      this.alignTitle = Alignment.bottomLeft});
```

4. Let's design a card in class GlassmorphismCardState

```dart

  @override
  Widget build(BuildContext context) {
    return Stack(
      children: [
        Container(
            height: height,
            width: width,
            decoration: BoxDecoration(
              color: backgroundColor.withOpacity(opacity),
              borderRadius: BorderRadius.circular(circular),
            ),
            child: null),
        Container(
            width: width - 5,
            height: height - 5,
            decoration: BoxDecoration(
                borderRadius: BorderRadius.circular(circular),
                border: Border(
                    bottom: BorderSide(width: borderSize, color: borderColor),
                    top: BorderSide(width: borderSize, color: borderColor),
                    left: BorderSide(width: borderSize, color: borderColor),
                    right: BorderSide(width: borderSize, color: borderColor))),
            child: Column(
              children: [
                SizedBox(
                  height: 20,
                ),
                Expanded(
                    flex: 1,
                    child: Container(
                      color: titleColor != null
                          ? titleColor!.withOpacity(opacity)
                          : null,
                      child: Align(alignment: alignTitle, child: title),
                    )),
                Expanded(
                    flex: 4,
                    child: Container(
                      padding: EdgeInsets.only(bottom: 10),
                      child: body ?? null,
                    ))
              ],
            )),
      ],
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
<<<<<<< HEAD

- My package: [GlassmorphismCard](https://pub.dev/packages/glassmorphismcard)
- Homepage: [TranLinh101h/glassmorphism_card](https://github.com/TranLinh101h/glassmorphism_card.git)
=======
>>>>>>> a6f6b202d3723d4ecc60709361805795184bd0c4
