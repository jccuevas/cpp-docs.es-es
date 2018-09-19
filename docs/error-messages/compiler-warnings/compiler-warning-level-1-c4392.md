---
title: Compilador advertencia (nivel 1) C4392 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4392
dev_langs:
- C++
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8632b91710668c44a75a4ba098c5da3790ba828f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073827"
---
# <a name="compiler-warning-level-1-c4392"></a>Advertencia del compilador (nivel 1) C4392

'firma': número incorrecto de argumentos para la función intrínseca, se esperaba 'número' argumentos

Una declaración de función para una función intrínseca del compilador tiene un número incorrecto de argumentos. La imagen resultante no funcionen correctamente.

Para corregir esta advertencia, corrija la declaración o eliminar la declaración y simplemente #include el archivo de encabezado adecuado.

El ejemplo siguiente genera C4392:

```
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