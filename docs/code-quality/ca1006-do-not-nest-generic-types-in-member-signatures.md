---
title: "CA1006: Do not nest generic types in member signatures"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords:
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
ms.workload:
  - "multiple"
---
# CA1006: Do not nest generic types in member signatures

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Category|Microsoft.Design|
|Breaking change|Breaking|

## Cause
An externally visible member has a signature that contains a nested type argument.

## Rule description
A nested type argument is a type argument that is also a generic type. To call a member whose signature contains a nested type argument, the user must instantiate one generic type and pass this type to the constructor of a second generic type. The required procedure and syntax are complex and should be avoided.

## How to fix violations
To fix a violation of this rule, change the design to remove the nested type argument.

## When to suppress warnings
Do not suppress a warning from this rule. Providing generics in a syntax that is easy to understand and use reduces the time that is required to learn and increases the adoption rate of new libraries.

## Example
The following example shows a method that violates the rule and the syntax that is required to call the violating method.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## Related rules
[CA1005: Avoid excessive parameters on generic types](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Collections should implement generic interface](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Do not declare static members on generic types](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Do not expose generic lists](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004: Generic methods should provide type parameter](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Use generic event handler instances](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Use generics where appropriate](../code-quality/ca1007-use-generics-where-appropriate.md)

## See also
[Generics](/dotnet/csharp/programming-guide/generics/index)