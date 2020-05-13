---
title: Advertencia del compilador (nivel 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 6dc5e2c7a40a276e225d030bc0340fb0bfe25bb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162730"
---
# <a name="compiler-warning-level-1-c4391"></a>Advertencia del compilador (nivel 1) C4391

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
