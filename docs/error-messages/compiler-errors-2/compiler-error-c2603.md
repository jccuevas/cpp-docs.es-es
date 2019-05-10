---
title: Error del compilador C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447995"
---
# <a name="compiler-error-c2603"></a>Error del compilador C2603

> '*función*': Hay demasiados objetos static en ámbito de bloque con constructores/destructores en la función

En las versiones de Microsoft C++ compilador antes de Visual Studio 2015, o cuando el [/Zc: threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) se especifica la opción del compilador, hay un límite de 31 en el número de objetos estáticos puede tener en visible externamente función insertada.

Para resolver este problema, se recomienda adoptar una versión más reciente de Microsoft C++ conjunto de herramientas del compilador, o si es posible, quite la opción del compilador/Zc: threadsafeinit. Si esto no es posible, considere la posibilidad de combinar los objetos estáticos. Si los objetos son del mismo tipo, considere la posibilidad de uso de una sola matriz estática de ese tipo y hacer referencia a miembros individuales según sea necesario.

## <a name="example"></a>Ejemplo

El código siguiente genera la advertencia C2603 y muestra cómo corregirlo:

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
