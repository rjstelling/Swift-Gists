# Swift Gists

This is a continiously expanding list of GitHub Gists (and repos) containing simple but useful Swift code. Nothing here realy warrents a Framework or Library but can be copied and pasted.

## Gists & Repositories

### [Fixing Linker Errors in Xcode (`___llvm_profile_runtime` Missing Symbol)](https://gist.github.com/rjstelling/be644d7d3061ac6e53894f2953385f3c)

This tutorial explains how to resolve the linker error ___llvm_profile_runtime missing symbol in Xcode, typically occurring when code coverage settings (CLANG_COVERAGE_MAPPING) are inadvertently enabled. The issue is common when using Swift Packages like PocketSVG. It guides you through verifying the problematic setting via command-line comparison of build settings, then demonstrates the solution—deleting the auto-generated test plan in Xcode’s test plan manager. After performing this simple step and cleaning your build, the linker error should be fixed.

### [How to Create and Use Multiple Apple IDs for iOS Simulator Testing](https://gist.github.com/rjstelling/bd783f50416f424c6080db911080a177)

Creating multiple Apple IDs for testing your app in the iOS Simulator can help isolate user experiences and troubleshoot issues effectively. Follow this easy guide to set up and successfully use multiple Apple IDs.

### [Creating a UIBarButtonItem That Ignores Smart Invert](https://gist.github.com/rjstelling/db5c49bf97a17ab7100233f807dd26d0)

This tutorial shows how to create a custom UIBarButtonItem that ignores the Smart Invert accessibility feature (using `accessibilityIgnoresInvertColors`). It also covers why using a UIImageView as the custom view will not trigger an action, and offers a helpful example of an accessibility hint.

### [Semantic Versioning](https://gist.github.com/rjstelling/dfa3e6ac491806a63e359259a9a06dc3)

A `Version` type that supports [Semantic Versioning](https://semver.org) with labels.

```swift
let version1: Version = "1.0.0"
let version2: Version = "2.0.0"

version1 == version2 // false
version2 > version1 // true

let version1point1 = "1.1"

version1.isCompatible(version1point1) // true
version2.isCompatible(version1point1) // false

let version2Prerelease = "2.0-beta"

version2Prerelease >= version2 //false
```

### [Swifty Uniform Type Identifier Extensions](https://gist.github.com/rjstelling/0e3298a42c2a2bca2f75f193578521c3)

A `URL` extension to make working with [UTIs](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/understanding_utis/understand_utis_intro/understand_utis_intro.html#//apple_ref/doc/uid/TP40001319-CH201-SW1) in Swift less painful.

```swift
let documentUrl = URL(fileURLWithPath: "/Volumes/MyDisk/Projects/Project1/Report.pages"
let uti = try doumentUrl.uniformTypeIdentifier()

print("\(uti)") // Pages Document
```

### [RegularExpressionValidation Property Wrapper](https://gist.github.com/rjstelling/649ff0e848af4e03f461386f4548b72d)

A `@propertyWrapper` that validates a string using a regular expression. If the string matches then it is assigned to the property if it does not then the property is net to nil. Also included is an example of validating email addresses.

Example:

```swift
struct Example {
    
    /* This will be set to nil unless the string assigned to it matches the regular expression 
    "^(?:[a-z0-9!#$%&'*+/=?^_`{|}~-]+(?:\\.[a-z0-9!#$%&'*+/=?^_`{|}~-]+)*|\"(?:[\\x01-\\x08\\x0b\\x0c\\x0e-\\x1f\\x21\\x23-\\x5b\\x5d-\\x7f]|\\[\\x01-\\x09\\x0b\\x0c\\x0e-\\x7f])*\")@(?:(?:[a-z0-9](?:[a-z0-9-]*[a-z0-9])?\\.)+[a-z0-9](?:[a-z0-9-]*[a-z0-9])?|\\[(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?|[a-z0-9-]*[a-z0-9]:(?:[\\x01-\\x08\\x0b\\x0c\\x0e-\\x1f\\x21-\\x5a\\x53-\\x7f]|\\[\\x01-\\x09\\x0b\\x0c\\x0e-\\x7f])+)\\])$"
    */
    @EmailValidation
    var email: String?
    
    // The string must be in the format $1,000,000.00 or £1,000,000.00
    // Missing $ or £ will fail, `.` and `,` are optional
    @RegularExpressionValidation("^[£$][0-9,]*$")
    var currency: String?    
}
```

### [Standard Streams](https://github.com/rjstelling/StandardStreams.swift)

A protocol based approach to writing to `Standard Out` and `Standard Error`.

```swift
let console = StandardOut()
let error = StandardErr()

console.print("Hello World! - This will print to stdout and can be piped or redirect to a file.")

error.print("Errors are by standard printed to the console even if your redirect, useful!")
```

### [Base Functions](https://gist.github.com/rjstelling/0216a4f9bfaec87dec44d30ac65399b1)

A set of extensions on `String` and `FixedWidthInteger` to encode and decode unsigned integers with custom character sets. 

```swift
// Encode integer to a string
let encodedValue = try 1973.encode() // "PZ"

// Decode the string back to an integer
let decodedValue: UInt = try encodedValue.decode() // 1973

// Using a custom string
let rosetta = "🤖❤️☠️🤓🦁🍆🧀😎🙄🤢🧠🧶🙈🙉🙊🔥🥕⚽️💊🎶🧶👏🔡"
let emojiEncoded = try 1024.encode(rosetta.count, using: rosetta) // "❤️👏🙈"

let emojiDecoded: UInt = try "❤️👏🙈".decode(UInt(rosetta.count), using: rosetta) // 1024
```

### [Fowler–Noll–Vo Hash](https://gist.github.com/rjstelling/fc695f5c37beeefd2a810179b723b29f)

Data Extension for Fowler–Noll–Vo hash function.

```swift
let data = "Hello World!".data(using: .utf8)!
let fnvValue = data.fnv32HashString() // "12a9a41c"

// Adding a single byte has a large affect on the hash
let fnvValue2 = (data + Data(repeating: 255, count: 1)).fnv32HashString() // "7d0d58eb"
```

### [Two Label UIButton](https://gist.github.com/rjstelling/70c4d0ad6934df99246c0f56e3494f38)

A simple Auto Layout solution for a UIButton with 2 labels.

```swift
let tlButton = TwoLabelButton()
tlButton.setTitles( ("Title:", "value") )
```

### [Print Binary String of Integers](https://gist.github.com/rjstelling/3be83e4b5dbdb8b6278e324780938400)

A generic function to print the "binary string" of any `FixedWidthInteger`.

Example:

```swift
let smallNumber: UInt16 = 7
print(asBinary: smallNumber) //output: 0b0000000000000111
```

## Future Improvements

1. Comments.
2. Examples.

## Pull Requests

If you feel like you want to, thats cool! However, I'm not promising to be speedy or meritocratic.

## Licence

All code, including this file are covered by the MIT Licence.


