---
title: Error del compilador C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 2b744729097f7e697c7a7695a849b5ee46d7a4ab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761037"
---
# <a name="compiler-error-c2920"></a>Error del compilador C2920

nueva definición: 'class': ya se ha declarado una clase de plantilla o genérica como 'type'

Una clase genérica o de plantilla tiene varias declaraciones que no son equivalentes. Para corregir este error, utilice nombres diferentes para los distintos tipos o quite la nueva definición del nombre de tipo.

El ejemplo siguiente genera el error C2920 y muestra cómo corregirlo:

```cpp
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

También se puede producir C2920 al utilizar genéricos:

```cpp
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```
