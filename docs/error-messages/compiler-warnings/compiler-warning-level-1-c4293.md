---
title: Compilador advertencia (nivel 1) C4293 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4293
dev_langs:
- C++
helpviewer_keywords:
- C4293
ms.assetid: babecd96-eb51-41a5-9835-462c7a46dbad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a29a42d5e06ededbcc4f16224b3e4332d56dbe03
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050210"
---
# <a name="compiler-warning-level-1-c4293"></a>Advertencia del compilador (nivel 1) C4293

'operator': desplazar un recuento negativo o demasiado grande; comportamiento impredecible

Si un valor de desplazamiento es negativo o demasiado grande, el comportamiento de la imagen resultante es indefinido.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4293:

```
// C4293.cpp
// compile with: /c /W1
unsigned __int64 combine (unsigned lo, unsigned hi) {

   return (hi << 32) | lo;   // C4293

   // try the following line instead
   // return ( (unsigned __int64)hi << 32) | lo;
}
```