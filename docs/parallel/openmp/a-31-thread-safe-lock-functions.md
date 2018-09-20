---
title: A.31 funciones de bloqueo de subprocesos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3ad89eb8-076c-405a-be5e-88d3d707a832
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c25e88b115cb1f82268040a8d17e0dc9eaed3fee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408983"
---
# <a name="a31---thread-safe-lock-functions"></a>A.31 Funciones lock seguras para subprocesos

En el ejemplo de C++ siguiente se muestra cómo inicializar una matriz de bloqueos en una región paralela mediante `omp_init_lock` ([sección 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) en la página 42).

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```