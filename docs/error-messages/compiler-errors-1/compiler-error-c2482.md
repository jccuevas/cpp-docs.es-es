---
title: Error del compilador C2482 | Documentos de Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3dd23069f389d0a02e10d26edb7ee4fd3c373cb
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256011"
---
# <a name="compiler-error-c2482"></a>Error del compilador C2482

>'*identificador*': la inicialización dinámica de datos 'thread' no se permite en código administrado o WinRT

## <a name="remarks"></a>Comentarios

En administrados o WinRT de código, las variables declaradas con el [__declspec (Thread)](../../cpp/thread.md) atributos de modificador de clase de almacenamiento o la [thread_local](../../cpp/storage-classes-cpp.md#thread_local) especificador de clase de almacenamiento no se puede inicializar con una expresión requiere la evaluación en tiempo de ejecución. Se requiere una expresión estática para inicializar `__declspec(thread)` o `thread_local` datos en estos entornos en tiempo de ejecución.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2482 en administrados (**/CLR**) y WinRT (**/ZW**) código:

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Para solucionar este problema, inicializar el almacenamiento local de subprocesos mediante el uso de una constante, **constexpr**, o una expresión estática. Realizar cualquier inicialización específicas de un subproceso por separado.