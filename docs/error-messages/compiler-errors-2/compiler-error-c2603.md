---
title: Error del compilador C2603 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2603
dev_langs:
- C++
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a893a77fb3760f00fb7fe7b5cb3ce5b3db3346e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057685"
---
# <a name="compiler-error-c2603"></a>Error del compilador C2603

> '*función*': hay demasiados objetos static en ámbito de bloque con constructores/destructores en la función

En las versiones del compilador de Visual C++ antes de Visual Studio 2015, o cuando el [/Zc: threadsafeinit](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) se especifica la opción del compilador, hay un límite de 31 en el número de objetos estáticos puede tener en una función insertada visible externamente .

Para resolver este problema, se recomienda adoptar una versión más reciente del conjunto de herramientas del compilador de Visual C++, o si es posible, quite la opción del compilador/Zc: threadsafeinit. Si esto no es posible, considere la posibilidad de combinar los objetos estáticos. Si los objetos son del mismo tipo, considere la posibilidad de uso de una sola matriz estática de ese tipo y hacer referencia a miembros individuales según sea necesario.

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
