---
title: Error del compilador C3010 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3010
dev_langs:
- C++
helpviewer_keywords:
- C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d68be11a510ba41197cb9645484a10ca8dae6d77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075129"
---
# <a name="compiler-error-c3010"></a>Error del compilador C3010

'etiqueta': no se permiten saltos fuera de un bloque estructurado de OpenMP.

No se puede saltar dentro o fuera del código un bloque OpenMP.

El ejemplo siguiente genera la advertencia C3010:

```
// C3010.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
      #pragma omp parallel
      {
         goto lbl3;
      }
   }
   lbl3:;   // C3010
}
```