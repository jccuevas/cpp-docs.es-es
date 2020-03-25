---
title: Advertencia del compilador C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: df6fc88ffe98dd2b4a3129800c7881f26d4f625b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164825"
---
# <a name="compiler-warning-c4986"></a>Advertencia del compilador C4986

' función ': la especificación de la excepción no coincide con la declaración anterior

Esta advertencia se puede generar cuando hay una especificación de excepción en una declaración y no en la otra.

De forma predeterminada, C4986 es OFF. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4986.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se elimina esta advertencia.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
