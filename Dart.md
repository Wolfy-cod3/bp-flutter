# Code GuideLines:

## 1. Naming Guidelines

It is a good practice to write code in such a way that it should be self-explanatory. 
The variables and functions should be named based on the operations they are assigned for.

### Packages
Packages and source files should be named using lowercase letters with an underscore. 
For example, a ‘test driver’ package should be named ‘test_driver’ 
while a package for ‘dependency injection’ should be named dependency_injection.

### Classes
Classes, enums, and parameters should be named using ‘Upper Camel Case’ letters with 
no underscore and where only the first letter of the word is capitalized. For example

                              class AuthViewModel {
                              …
                              }
                              enum AuthStatus {
                              success,
                              failed,
                              error
                              }
Also, the filename should be lowercase with an underscore. For example auth_view_model.dart

### Methods & Variables

Similar to classes, methods and variables should also be named in camel case, but in Lower Camel Case. 
For example var userProfile; and void loadUserProfile() {}

## 2. Ordering Guidelines

Every section should be in order, and separated by an empty line.

### Order of class property

public class myClass
{
#region Private Members
#endregion
#region Public Properties
#endregion
#region Constructors
#endregion
#region Public Methods
#endregion
}

### Order of imports/export sections

#### dart import ‘package:dltwallet/src/appflow/main_flow/main_tab.dart’;
import ‘package:dltwallet/src/appflow/splash_screen.dart’;
export ‘package:async/src/error.dart’;imports must come before other imports

import ‘dart:async’;
import ‘dart:html’;
import ‘package:model/UserModel.dart’;
import ‘package:network/HttpRequest.dart’

#### export should be after other imports

import ‘package:dltwallet/src/appflow/main_flow/main_tab.dart’;
import ‘package:dltwallet/src/appflow/splash_screen.dart’;
export ‘package:async/src/error.dart’;

## 3. Formating Guidelines

Improve source code readability and understandability, and conform 
to a standard style. This can help avoid introducing errors in the code.

### Format code using ‘dartfmt’
Dart provides an advanced automated code formatter called dartfmt that does 
the job for you. Using dartfmt, you can remove the official whitespace.

### Make your code more formatter-friendly
Code structure and naming should be as simple as possible.

### Use 80 characters in a line
Otherwise your code is likely to be too wordy or could be a harder to read.
Methods shouldn’t have more than an average of 30 code lines, excluding line spaces and comments.

## 4. Practice Coding

### Use const keyword

Dart 2 introduced optional parameters for constructors. The const keyword is also optional where it
can be understood by the compiler.There are different ways that a const keyword can be used as shown below:
#### A const collection literal.
#### A const constructor call.
#### As a metadata annotation.
#### As an initializer for a variable declaration.

### Return ‘Widget’

We can return Widget instead of Flutter Widget. As your project evolves, you 
may change the widget type that is returned by your function. Let us take an example: 
you may prefer to wrap your widget with Center(). By returning a widget, refactoring is simplified, since the 
method signature does not change. For Example:

Widget returnContainerWidget() {
return Center(child: Container());
}

### Boolean

We can use the null check operator ‘??’ to convert null to a boolean value. We must convert the null value to either 
true or false. Although you could do this using ‘==’, using the ‘??’ operator instead is easier to use, and reduces 
lines of code used.

userProfile?.isEnabled ?? false;

### Use ‘=>’ function expression

You can use ‘=>’ for simple members like calculate and return value.If you are using more than one line or your code has
nested expressions, then you can use a block body and a few statements

double get driveTime(double startTime, double endTime) ‘=>’ endTime-startTime;

### Use async/await

For raw future functions, use aync/await. Any function you want to run asynchronously must have the async modifier added 
to it. When you are adding the await modifier, the code is explicitly saying: “don’t go further until my future is completed”.

function () async {
var data = await loadData();
// Do something…
}

# Code tips:

## 1. Dart supports string multiplication.

You can use this to check how a long string fits inside a Text widget:
Text('You have pushed the button this many times:' * 5)

## 2. Need to execute multiple Futures concurrently? Use Future.wait.

Consider this mock API class that tells us the latest numbers of COVID cases:

            // Mock API class
            class CovidAPI {
              Future<int> getCases() => Future.value(1000);
              Future<int> getRecovered() => Future.value(100);
              Future<int> getDeaths() => Future.value(10);
            }
To execute all these futures concurrently, use Future.wait. This takes a list or 
futures and returns a future of lists:

final api = CovidAPI();
final values = await Future.wait([
    api.getCases(),
    api.getRecovered(),
    api.getDeaths(),
]);
print(values); // [1000, 100, 10]
This is ideal when the futures are independent, and they don't need to execute sequentially.

## 3. Implement a "call" method in your Dart classes to make them callable like a function.

class PasswordValidator {
  bool call(String password) {
    return password.length > 10;
  }
}

final validator = PasswordValidator();
// can use it like this:
validator('test');
validator('test1234');
// no need to use it like this:
validator.call('not-so-frozen-arctic');

## 4. Need to invoke a callback but only if it's not null? Use the "?.call()" syntax.

void _dragComplete() {
    if (onDragCompleted != null) {
      onDragCompleted();
    }
  }
  But there is a simpler way (note the use of ?.):
  Future<void> _dragComplete() async {
    onDragCompleted?.call();
  }

# More sources, please look into these:
  https://codewithandrea.com/tips/dart-flutter-easy-wins-1-7/
  https://dart.dev/tools/linter-rules
  https://dart.dev/guides/language/effective-dart
  https://dart.dev/guides/language/effective-dart/design
