---
title: Error del compilador C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: 8dc7b521243c4eafdc22fab851812b6c12b004cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755920"
---
# <a name="compiler-error-c2146"></a>Error del compilador C2146

error de sintaxis: falta ' token ' delante del identificador ' Identifier '

El compilador esperaba `token` y se encontró `identifier` en su lugar.  Posibles causas:

1. Error ortográfico o de capitalización.

1. Falta el especificador de tipo en la declaración del identificador.

Este error puede deberse a un error tipográfico. El error [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) suele preceder a este error.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2146.

```cpp
// C2146.cpp
class CDeclaredClass {};

class CMyClass {
   CUndeclared m_myClass;   // C2146
   CDeclaredClass m_myClass2;   // OK
};

int main() {
   int x;
   int t x;   // C2146 : missing semicolon before 'x'
}
```

## <a name="example"></a>Ejemplo

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: falta la palabra clave `typename`.

En el ejemplo siguiente se compila en Visual Studio .NET 2002, pero se producirá un error en Visual Studio .NET 2003:

```cpp
// C2146b.cpp
// compile with: /c
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};

template <typename T>
X<T>::Y func() { }   // C2146

// OK
template <typename T>
typename X<T>::Y func() { }
```

## <a name="example"></a>Ejemplo

También verá este error como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: las especializaciones explícitas ya no encuentran parámetros de plantilla de la plantilla principal.

No se permite el uso de `T` de la plantilla principal en la especialización explícita. Para que el código sea válido en Visual Studio .NET 2003 y Visual Studio .NET, reemplace todas las instancias del parámetro de plantilla de la especialización por el tipo especializado explícitamente.

En el ejemplo siguiente se compila en Visual Studio .NET, pero se producirá un error en Visual Studio .NET 2003:

```cpp
// C2146_c.cpp
// compile with: /c
template <class T>
struct S;

template <>
struct S<int> {
   T m_t;   // C2146
   int m_t2;   // OK
};
```
