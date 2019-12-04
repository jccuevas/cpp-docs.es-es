---
title: Error del compilador C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 1c58c2d5da0049ec670e11c930b397caec3cbbee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751526"
---
# <a name="compiler-error-c2990"></a>Error del compilador C2990

' Class ': tipo que no es de clase ya se ha declarado como un tipo de clase

La clase no genérica o de plantilla redefine una clase genérica o de plantilla. Compruebe si hay conflictos en los archivos de encabezado.

En el ejemplo siguiente se genera C2990:

```cpp
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 también puede producirse cuando se usan genéricos:

```cpp
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 también puede producirse debido a un cambio importante en el C++ compilador de Microsoft para Visual Studio 2005; Ahora, el compilador requiere que varias declaraciones del mismo tipo sean idénticas con respecto a la especificación de plantilla.

En el ejemplo siguiente se genera C2990:

```cpp
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```
