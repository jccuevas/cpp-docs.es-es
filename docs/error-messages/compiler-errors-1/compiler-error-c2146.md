---
title: Error del compilador C2146
ms.date: 11/04/2016
f1_keywords:
- C2146
helpviewer_keywords:
- C2146
ms.assetid: 6bfb7de6-6723-4486-9350-c66ef88d7a64
ms.openlocfilehash: f00de0ce491d517da11f251b89ccb9a7ae66b77d
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447274"
---
# <a name="compiler-error-c2146"></a>Error del compilador C2146

error de sintaxis: falta 'token' delante del identificador 'identificador'

El compilador esperado `token` y encontrar `identifier` en su lugar.  Causas posibles:

1. Error de ortografía ni de mayúsculas y minúsculas.

1. Falta el especificador de tipo en la declaración del identificador.

Este error puede deberse a un error tipográfico. Error [C2065](../../error-messages/compiler-errors-1/compiler-error-c2065.md) normalmente precede a este error.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2146.

```
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

Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: faltan `typename` palabra clave.

El ejemplo siguiente se compila en Visual Studio .NET 2002, pero se producirá un error en Visual Studio .NET 2003:

```
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

También verá este error como resultado del trabajo de conformidad del compilador efectuado para Visual Studio .NET 2003: las especializaciones explícitas ya no buscan parámetros de plantilla desde la plantilla principal.

El uso de `T` no se permite en la especialización explícita de la plantilla principal. Para que el código sea válido en el Visual Studio .NET 2003 y Visual Studio. NET, reemplace todas las instancias del parámetro de plantilla en la especialización por el tipo especializado explícitamente.

En el ejemplo siguiente se compila en Visual Studio. NET, pero se producirá un error en Visual Studio .NET 2003:

```
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