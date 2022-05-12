---
description: How to use Swift as shell script language.
---

# Scripting Swift

Swift not only allows you to write compiled applications with or without UI interaction, but also is able to be run as command line shell scripts.

Simply start a new Swift file by adding the usual `#! …` front matter as the first line of your source code and add the path to the location of the `swiftc` command — and you're set. Here is a practical example:

```swift
#!/usr/bin/swift

/*
 Some nice formatting while printing to the console. We use ANSI TTY escape sequences and colour codes here. `CustomStringConvertible` makes the handling of the struct much easier.
 */
enum Colour: String, CustomStringConvertible {
	var description: String {
		self.rawValue
	}

	case reset = "\u{1b}[0m"
	case colourReset = "\u{1b}[39;49m"
	case bold = "\u{1b}[1m"
	case red = "\u{1b}[37;41m"
	case green = "\u{1b}[37;42m"
	case blue = "\u{1b}[37;44m"
}

print("\(Colour.blue)\(Colour.bold) Hello, \(Colour.red) Swift! \(Colour.reset)")
```

Save the file as — for example — `hello_swift.swift` and make it executable by setting the corresponding flag:

```bash
chmod u+x hello_swift.swift
```

You then can execute the Swift script by dotting it like so:

```bash
./hello_swift.swift
```

Please find my Swift scripts in the corresponding [GitHub](https://github.com/MatiMax/swift) repository.
