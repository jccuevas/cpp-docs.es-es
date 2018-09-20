---
title: NOWAIT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- nowait
dev_langs:
- C++
helpviewer_keywords:
- nowait OpenMP clause
ms.assetid: 8a74265d-879c-46cf-8071-a1084f24f16e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fa4579aabf8a62e5117e096c5a49225451af6e7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381067"
---
# <a name="nowait"></a>nowait

Invalida la barrera implícita en una directiva.

## <a name="syntax"></a>Sintaxis

```
nowait
```

## <a name="remarks"></a>Comentarios

`nowait` se aplica a las siguientes directivas:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Secciones](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

Para obtener más información, consulte [2.4.1 for (construcción)](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections (construcción)](../../../parallel/openmp/2-4-2-sections-construct.md), y [2.4.3 single construir](../../../parallel/openmp/2-4-3-single-construct.md).

## <a name="example"></a>Ejemplo

```
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="see-also"></a>Vea también

[Cláusulas](../../../parallel/openmp/reference/openmp-clauses.md)