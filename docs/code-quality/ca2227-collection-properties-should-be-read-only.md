---
title: "CA2227: Collection properties should be read only"
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords:
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
 - CSharp
 - VB
 - CPP
ms.workload:
  - "multiple"
---
# CA2227: Collection properties should be read only

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|Breaking change|Breaking|

## Cause

An externally visible, writable property is of a type that implements <xref:System.Collections.ICollection?displayProperty=fullName>. This rule ignores arrays, indexers (properties with the name 'Item'), and permission sets.

## Rule description

A writable collection property allows a user to replace the collection with a completely different collection. A read-only property stops the collection from being replaced, but still allows the individual members to be set. If replacing the collection is a goal, the preferred design pattern is to include a method to remove all the elements from the collection, and a method to repopulate the collection. See the <xref:System.Collections.ArrayList.Clear%2A> and <xref:System.Collections.ArrayList.AddRange%2A> methods of the <xref:System.Collections.ArrayList?displayProperty=fullName> class for an example of this pattern.

Both binary and XML serialization support read-only properties that are collections. The <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> class has specific requirements for types that implement <xref:System.Collections.ICollection> and <xref:System.Collections.IEnumerable?displayProperty=fullName> in order to be serializable.

## How to fix violations

To fix a violation of this rule, make the property read-only. If the design requires it, add methods to clear and repopulate the collection.

## When to suppress warnings

You can suppress the warning if the property is part of a [Data Transfer Object (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) class.

Otherwise, do not suppress warnings from this rule.

## Example

The following example shows a type with a writable collection property and shows how the collection can be replaced directly. Additionally, it shows the preferred manner of replacing a read-only collection property using `Clear` and `AddRange` methods.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## Related rules

- [CA1819: Properties should not return arrays](../code-quality/ca1819-properties-should-not-return-arrays.md)