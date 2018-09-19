---
title: Error del compilador C3039 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b225103cf45331688a65d4528cadb39e730c75c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098100"
---
# <a name="compiler-error-c3039"></a>Error del compilador C3039

'var': la variable de índice de la instrucción 'for' de OpenMP no puede ser una variable de reducción

Una variable de índice es implícitamente privada, por lo que no se puede usar la variable en una cláusula [reduction](../../parallel/openmp/reference/reduction.md) en la directiva [parallel](../../parallel/openmp/reference/parallel.md) envolvente.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3039:

```
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```