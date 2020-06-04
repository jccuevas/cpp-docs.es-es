---
title: Error del compilador C3856
ms.date: 11/04/2016
f1_keywords:
- C3856
helpviewer_keywords:
- C3856
ms.assetid: 242d9322-c325-4f20-be58-b2be6da56d60
ms.openlocfilehash: 6079eb0a2b453c3eef159ed8a0d8536a0ad667b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754841"
---
# <a name="compiler-error-c3856"></a>Error del compilador C3856

' type ': la clase no es un tipo de clase

La causa más común de este error es cuando hay más listas de parámetros genéricos o de plantilla en el punto de definición que en el punto de declaración.

En el ejemplo siguiente se genera C3856:

```cpp
// C3856.cpp
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>   // C3856
template <class T1>
template <class T2>  // extra template parameter list in definition
struct S<T>::S1{};
```

Solución posible:

```cpp
// C3856b.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1;
   void f();
};

template <class T>
template <class T1>
struct S<T>::S1{};
```

C3856 también puede producirse cuando se usan genéricos:

```cpp
// C3856c.cpp
// compile with: /clr
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GS<T>::GS2 {};   // C3856
```

Solución posible:

```cpp
// C3856d.cpp
// compile with: /clr /c
generic <class T>
ref struct GS {
   generic <class U>
   ref struct GS2;
};

generic <class T>
generic <class U>
ref struct GS<T>::GS2 {};
```
