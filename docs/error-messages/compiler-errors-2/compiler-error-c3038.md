---
title: Error del compilador C3038 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3038
dev_langs:
- C++
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dfdfe8ce50765bf4f94bff7acb0837ddb3fd8ca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057995"
---
# <a name="compiler-error-c3038"></a>Error del compilador C3038

'var': la variable de la cláusula 'private' no puede ser una variable de reducción en el contexto envolvente

Las variables que aparecen en la cláusula [reduction](../../parallel/openmp/reference/reduction.md) de una directiva paralela no pueden especificarse en una cláusula [private](../../parallel/openmp/reference/private-openmp.md) en una directiva de uso compartido que se enlaza a la construcción paralela.

El ejemplo siguiente genera la advertencia C3038:

```
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```