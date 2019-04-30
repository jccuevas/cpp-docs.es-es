---
title: Error del compilador C3813
ms.date: 11/04/2016
f1_keywords:
- C3813
helpviewer_keywords:
- C3813
ms.assetid: ffdbc489-71bf-4cd6-988c-f824c9ab3ceb
ms.openlocfilehash: 302b21d709424cda50abd0247f7b82048511cd73
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384314"
---
# <a name="compiler-error-c3813"></a>Error del compilador C3813

una declaración de propiedad solo puede aparecer en la definición de un tipo WinRT o administrado

Un [propiedad](../../dotnet/how-to-use-properties-in-cpp-cli.md) sólo puede declararse dentro de un administrado o en tiempo de ejecución de Windows tipo. Los tipos nativos no admiten la palabra clave `property`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C3813 y se muestra cómo corregirlo:

```cpp
// C3813.cpp
// compile by using: cl /c /clr C3813.cpp
class A
{
   property int Int; // C3813
};

ref class B
{
   property int Int; // OK - declared within managed type
};
```