---
title: Error del compilador C2989
ms.date: 11/04/2016
f1_keywords:
- C2989
helpviewer_keywords:
- C2989
ms.assetid: 936303d8-eb3b-4746-82ec-2f18020a6f64
ms.openlocfilehash: 585823c2114befa3e6d432e3cf8100fa14ed1a7d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176733"
---
# <a name="compiler-error-c2989"></a>Error del compilador C2989

' Class ': el tipo de clase ya se ha declarado como un tipo que no es de clase

La clase genérica o plantilla redefine una clase no genérica o no de plantilla. Compruebe si hay conflictos en los archivos de encabezado.

En el ejemplo siguiente se genera C2989:

```cpp
// C2989.cpp
// compile with: /c
class C{};

template <class T>
class C{};  // C2989
class C2{};
```

C2989 también puede producirse cuando se usan genéricos:

```cpp
// C2989b.cpp
// compile with: /clr /c
ref class GC1;

generic <typename T> ref class GC1;   // C2989
template <typename T> ref class GC2;

generic <typename T> ref class GC2;   // C2989
generic <typename T> ref class GCb;
template <typename T> ref class GC2;
generic <typename T> ref class GCc;
```
