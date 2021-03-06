---
description: >-
  Format arbitrarily complex blocks of code according to the source files
  defined styles.
---

# AutoFormat

`AutoFormat` performs whitespace formatting and indentation alignment on a defined sub-tree based on the project's style. This refactoring visitor is a building block for more complex visitors, so it does not have a declarative form.

`AutoFormat` uses an internal set of heuristics to inspect neighboring code and infer a style from it so that a changed block of code is as _locally_ consistent with the formatting of code as possible. In the absence of sufficient local evidence of a style, it falls back on the styles attached to the `J.CompilationUnit`. See [styles](../parsing-java-code.md#styles) for how to define styles on the source file.

## Java Definition

Rather than worrying about all the details of how a piece of code we are transforming is going to look \(especially when the transformation is complex\), you can just generate any sort of code, forget about formatting, and chain `AutoFormat` after your fixes to clean the result up.

```java
public class ComplexMethodTransformation extends JavaRefactorVisitor {
  public J visitMethodDecl(J.MethodDecl method) {
    // do some things to modify the method declaration
    // or body in some significant way and don't worry about formatting...

    // this will fix the indentation of the method declaration to be consistent with its surroundings
    andThen(new AutoFormat(method));

    return super.visitMethodDecl(method);
  }
}
```

## Example

Applying `AutoFormat` to the following class. Before:

```java
class A {
String a;
void setA(String value) {
a = value;
}
}
```

After:

```java
class A {
    String a;
    void setA(String value) {
        a = value;
    }
}
```

