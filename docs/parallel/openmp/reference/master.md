---
title: principal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- master
dev_langs:
- C++
helpviewer_keywords:
- master OpenMP directive
ms.assetid: 559ed974-e02a-486e-a23f-31556429b2c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9472854e22b1a1f7c4a13316244554b473f48298
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423733"
---
# <a name="master"></a>master

Especifica que sólo el maestro threadshould ejecutar una sección del programa.

## <a name="syntax"></a>Sintaxis

```
#pragma omp master
{
   code_block
}
```

## <a name="remarks"></a>Comentarios

El **maestro** directiva es compatible con ningún cláusulas de OpenMP.

El [único](../../../parallel/openmp/reference/single.md) directiva le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.

Para obtener más información, consulte [2.6.1 master construcción](../../../parallel/openmp/2-6-1-master-construct.md).

## <a name="example"></a>Ejemplo

```
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="see-also"></a>Vea también

[Directivas](../../../parallel/openmp/reference/openmp-directives.md)