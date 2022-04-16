# Solve problems and familiarize yourself with the GitHub process

## Request

- Solve the problem of isuse#16 in the repository [ltdangkhoa
/
Flutter-Animation-Progress-Bar](https://github.com/ltdangkhoa/Flutter-Animation-Progress-Bar/issues/16#issue-comment-box)
- Working with Github Processes

## Solution

### Solve the problem of isuse#16

In the package, I changed the int type to double of the currentValue and maxValue variables in the FAProgressBar class

```dart
class FAProgressBar {

  final double currentValue;
  final double maxValue;
```

And then I changed the toInt() function to toDouble() on line 146 to display decimals

```dart
   child: Text(
          (animation.value * widget.maxValue).toDouble().toString() +
              widget.displayText!,
          softWrap: false,
          style: widget.displayTextStyle,
        ),
```

### Working with Github Processes

- fork repo

- clone fork repo

- check out new branch

- code changed

- push to fork repo

- pull request to main branch

## Conclusion
<p>
After completing this task I learned how to work with the Github process
</p>
