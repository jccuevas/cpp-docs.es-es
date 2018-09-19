---
title: Error del compilador C3053 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3053
dev_langs:
- C++
helpviewer_keywords:
- C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c50112be2650c4b379b6de93acaa73a9cb285687
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112036"
---
# <a name="compiler-error-c3053"></a>Error del compilador C3053

'symbol': 'threadprivate' solo tiene valor válido para elementos de datos globales o estáticos

Símbolos pasan a [threadprivate](../../parallel/openmp/reference/threadprivate.md) deben ser globales o estáticos.

El ejemplo siguiente genera la advertencia C3053:

```
// C3053.cpp
// compile with: /openmp
void Test() {
   int x, y;
   #pragma omp threadprivate(x, y)   // C3053
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Posible resolución:

```
// C3053b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)

void Test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```