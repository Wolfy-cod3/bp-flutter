# bp-flutter
Best Practices Flutter 03.2023 v1 by W47

###  a) Dart Best Practices

# 1.Naming Guidelines

It is a good practice to write code in such a way that it should be self-explanatory. 
The variables and functions should be named based on the operations they are assigned for.

## Packages
Packages and source files should be named using lowercase letters with an underscore. 
For example, a ‘test driver’ package should be named ‘test_driver’ 
while a package for ‘dependency injection’ should be named dependency_injection.

## Classes
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
