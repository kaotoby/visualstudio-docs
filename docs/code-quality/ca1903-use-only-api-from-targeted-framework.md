---
title: "CA1903: Use only API from targeted framework"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords:
  - "UseOnlyApiFromTargetedFramework"
  - "CA1903"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1903: Use only API from targeted framework

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Category|Microsoft.Portability|
|Breaking change|Breaking - when fired against the signature of an externally visible member or type.<br /><br /> Non-Breaking - when fired in the body of a method.|

## Cause
A member or type is using a member or type that was introduced in a service pack that was not included with the project's targeted framework.

## Rule description
New members and types were included in .NET Framework 2.0 Service Pack 1 and 2, .NET Framework 3.0 Service Pack 1 and 2, and .NET Framework 3.5 Service Pack 1. Projects that target the major versions of the .NET Framework can unintentionally take dependencies on these new APIs. To prevent this dependency, this rule fires on usages of any new members and types that were not included by default with the project's target framework.

**Target Framework and Service Pack Dependencies**

|||
|-|-|
|When target framework is|Fires on usages of members introduced in|
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|
|.NET Framework 3.5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/A|

To change a project's target framework, see [How to: Target a version of .NET](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## How to fix violations
To remove the dependency on the service pack, remove all usages of the new member or type. If this is a deliberate dependency, either suppress the warning or turn off this rule.

## When to suppress warnings
Do not suppress a warning from this rule if this was not a deliberate dependency on the specified service pack. In this situation, your application might fail to run on systems without this service pack installed. Suppress the warning or turn off this rule if this was a deliberate dependency.

## Example
The following example shows a class that uses the type DateTimeOffset that is only available in .NET 2.0 Service Pack 1. This example requires that .NET Framework 2.0 has been selected in the Target Framework drop-down list in the Project properties.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## Example
The following example fixes the previously described violation by replacing usages of the DateTimeOffset type with the DateTime type.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## See also

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Framework targeting overview](../ide/visual-studio-multi-targeting-overview.md)