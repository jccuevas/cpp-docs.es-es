---
title: ADVERTENCIA del compilador (nivel 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 60b68906697f76d56ff6c0e13f1b4ec105ef1c25
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966116"
---
# <a name="compiler-warning-level-1-c4391"></a>ADVERTENCIA del compilador (nivel 1) C4391

' Signature ': tipo de valor devuelto incorrecto para la función intrínseca; se esperaba ' type '

Una declaración de función para un intrínseco del compilador tenía un tipo de valor devuelto incorrecto. Es posible que la imagen resultante no se ejecute correctamente.

Para corregir esta advertencia, corrija la declaración o elimine la declaración y simplemente #include el archivo de encabezado adecuado.

En el ejemplo siguiente se genera C4391:

```cpp
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```