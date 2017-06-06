---
title:  "JavaScript Style Guide"
categories: javascript
---

#### Indenting and whitespace
Use an indent of 2 spaces, with no tabs.

Lines should have no trailing whitespace at the end.

Blank lines improve readability by setting off sections of code that are logically related.

All text files should end in a single newline (\n). This avoids "\ No newline at end of file" warnings.

#### Operators
All binary operators (operators that come between two values), such as +, -, =, !=, ==, >, etc. should have a space before and after the operator, for readability. 

For example, an assignment should be formatted as foo = bar; rather than foo=bar;. Unary operators (operators that operate on only one value), such as ++, should not have a space between the operator and the variable or number they are operating on.

#### Control structures
Control structures include if, for, while, switch, etc

Control statements should have one space between the control keyword and opening parenthesis, to distinguish them from function calls.

Always use curly braces even in situations where they are technically optional. Having them increases readability and decreases the likelihood of logic errors being introduced when new lines are added. The opening curly should be on the same line as the opening statement, preceded by one space. The closing curly should be on a line by itself and indented to the same level as the opening statement.

```
if (something != somethingElse) {
		// …
	}
```

#### Line length and wrapping
In general, all lines of code should not be longer than 80 characters. If a statement does not fit on one line, the best place to break it, is after an operator or a comma.

```
document.getElementById("demo").innerHTML =
    "Hello Dolly."; 
```

Lines containing longer function names, function/class definitions, variable declarations, etc are allowed to exceed 80 characters.

Control structure conditions may exceed 80 characters, if they are simple to read and understand.

#### Naming conventions

Variable and function names should be written as camelCase
Constants (like PI) should be written in UPPERCASE
