# ArgumentMatchersAny

Between Mockito 1.x and Mockito 2.x, the method `org.mockito.Matchers.anyVararg` moved to the type `org.mockito.ArgumentMatchers` and changed names to `any`.

This visitor changes method references to reflect this refactoring.

## YAML Definition

The `org.openrewrite.java.Mockito` recipe includes this visitor. Here is how to include this visitor in a custom recipe you define called `com.yourorg.MyCustomRecipe`:

```yaml
---
type: specs.openrewrite.org/v1beta/recipe
name: com.yourorg.MyCustomRecipe 
visitors:
  - org.openrewrite.java.mockito.ArgumentMatchersAny
```

