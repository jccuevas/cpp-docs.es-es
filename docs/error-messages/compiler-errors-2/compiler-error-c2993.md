---
title: Error del compilador C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761236"
---
# <a name="compiler-error-c2993"></a>Error del compilador C2993

' Identifier ': tipo no válido para el parámetro de plantilla sin tipo ' Parameter '

No se puede declarar una plantilla con un argumento de estructura o Unión. Use punteros para pasar estructuras y uniones como parámetros de plantilla.

En el ejemplo siguiente se genera C2993:

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

Este error también se generará como resultado del trabajo de conformidad del compilador realizado en Visual Studio .NET 2003: ya no se permiten parámetros de plantilla de punto flotante sin tipo. El C++ estándar no permite parámetros de plantilla de punto flotante sin tipo.

Si es una plantilla de función, use un argumento de función para pasar el parámetro de plantilla sin tipo de punto flotante (este código será válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de C++visual). Si se trata de una plantilla de clase, no hay una solución sencilla.

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
