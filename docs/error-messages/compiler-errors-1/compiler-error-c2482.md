---
title: Error del compilador C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 5afa81369b2cf329baae02bc1309587015946409
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205158"
---
# <a name="compiler-error-c2482"></a>Error del compilador C2482

>'*Identifier*': no se permite la inicialización dinámica de datos ' Thread ' en código administrado o WinRT

## <a name="remarks"></a>Observaciones

En código administrado o WinRT, las variables declaradas mediante el atributo modificador de clase de almacenamiento [__declspec (Thread)](../../cpp/thread.md) o el especificador de clase de almacenamiento [thread_local](../../cpp/storage-classes-cpp.md#thread_local) no se pueden inicializar con una expresión que requiera evaluación en tiempo de ejecución. Se requiere una expresión estática para inicializar `__declspec(thread)` o `thread_local` datos en estos entornos en tiempo de ejecución.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2482 en el código administrado ( **/CLR**) y en WinRT ( **/ZW**):

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

Para corregir este problema, inicialice el almacenamiento local de subprocesos mediante una constante, **constexpr**o una expresión estática. Realice cualquier inicialización específica del subproceso por separado.
