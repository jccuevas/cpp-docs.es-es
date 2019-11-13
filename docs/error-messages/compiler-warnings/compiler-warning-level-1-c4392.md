---
title: ADVERTENCIA del compilador (nivel 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: b19080f4a86267a48618a5f40d7576c07c96c18a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966105"
---
# <a name="compiler-warning-level-1-c4392"></a>ADVERTENCIA del compilador (nivel 1) C4392

' Signature ': número incorrecto de argumentos para la función intrínseca, se esperaban argumentos ' Number '

Una declaración de función para un intrínseco del compilador tenía un número de argumentos incorrecto. Es posible que la imagen resultante no se ejecute correctamente.

Para corregir esta advertencia, corrija la declaración o elimine la declaración y simplemente #include el archivo de encabezado adecuado.

En el ejemplo siguiente se genera C4392:

```cpp
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```