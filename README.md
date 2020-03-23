This is a continiously expanding list of GitHub Gists containing simple but useful Swift code. Nothing here realy warrents a Framework or Library but can be copied and pasted. 

## Gists

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

A protocol based approch to writing to `Standard Out` and `Standard Error`.

### [Base Functions](https://gist.github.com/rjstelling/0216a4f9bfaec87dec44d30ac65399b1)

Encode and Decode Base N with custom character sets. 

### [Fowler–Noll–Vo Hash](https://gist.github.com/rjstelling/fc695f5c37beeefd2a810179b723b29f)

Data Extension for Fowler–Noll–Vo hash function.

### [Two Label UIButton](https://gist.github.com/rjstelling/70c4d0ad6934df99246c0f56e3494f38)

A simple Auto Layout solution for a UIButton with 2 labels.

### [Print Binary String of Integers](https://gist.github.com/rjstelling/3be83e4b5dbdb8b6278e324780938400)

A generic function to print the "binary string" of any `FixedWidthInteger`.

Example:

```swift
let smallNumber: UInt16 = 7
print(asBinary: smallNumber) //output: 0b0000000000000111
```

## Future Improvements

1. Comments.

## Pull Requests

If you feel like you want to, thats cool! However, I'm not promising to be speedy or meritocratic.

## Licence

All code, including this file are covered by the MIT Licence.


