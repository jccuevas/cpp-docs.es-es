---
title: A.9 usar directivas single | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a3a201450d54355aa96f0ea712ad9fa0f70f63f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448095"
---
# <a name="a9---using-single-directives"></a>A.9 Usar directivas single

En el ejemplo siguiente se muestra el `single` directiva ([sección 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) en la página 15). En el ejemplo, un solo subproceso (normalmente, el primer subproceso que se encuentra el `single` directiva) imprime el mensaje de progreso. El usuario no debe hacer ninguna suposición como a qué subproceso ejecutará el `single` sección. Todos los demás subprocesos se omitirá la `single` sección y detenerse en la barrera al final de la `single` construir. Si otros subprocesos puedan continuar sin esperar el subproceso que ejecuta el `single` sección, un `nowait` cláusula se puede especificar en el `single` directiva.

```
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```