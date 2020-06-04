---
title: Advertencia del compilador (nivel 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: a62bfdb6b9b29abf047e7690179978cb9516d477
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186886"
---
# <a name="compiler-warning-level-1-c4392"></a>Advertencia del compilador (nivel 1) C4392

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
