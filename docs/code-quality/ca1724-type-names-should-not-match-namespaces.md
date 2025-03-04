---
title: "CA1724: Type Names Should Not Match Namespaces"
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords:
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
  - "multiple"
---
# CA1724: Type names should not match namespaces

|||
|-|-|
|TypeName|TypeNamesShouldNotMatchNamespaces|
|CheckId|CA1724|
|Category|Microsoft.Naming|
|Breaking change|Breaking|

## Cause

A type name matches a referenced namespace name that has one or more externally visible types. The name comparison is case-insensitive.

## Rule description

User-created type names should not match the names of referenced namespaces that have externally visible types. Violating this rule can reduce the usability of your library.

## How to fix violations

Rename the type such that it doesn't match the name of a referenced namespace that has externally visible types.

## When to suppress warnings

For new development, no known scenarios occur where you must suppress a warning from this rule. Before you suppress the warning, carefully consider how the users of your library might be confused by the matching name. For shipping libraries, you might have to suppress a warning from this rule.