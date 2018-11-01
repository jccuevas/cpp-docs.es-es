---
title: Error del compilador C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564819"
---
# <a name="compiler-error-c2482"></a>Error del compilador C2482

>'*identificador*': inicialización dinámica de datos 'thread' no se permite en código administrado o WinRT

## <a name="remarks"></a>Comentarios

En administrados o WinRT de código, las variables declaradas con el [__declspec (Thread)](../../cpp/thread.md) atributos de modificador de clase de almacenamiento o la [thread_local](../../cpp/storage-classes-cpp.md#thread_local) especificador de clase de almacenamiento no se puede inicializar con una expresión que requiere la evaluación en tiempo de ejecución. Se requiere una expresión estática para inicializar `__declspec(thread)` o `thread_local` datos en estos entornos en tiempo de ejecución.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2482 en administrado (**/CLR**) y, en WinRT (**/ZW**) código:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Para corregir este problema, inicialice el almacenamiento local de subprocesos mediante el uso de una constante, **constexpr**, o una expresión estática. Realizar cualquier inicialización específica de subprocesos por separado.