---
title: Parallel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38b5bd4d277987be78cbd3714302c8b7f704b90f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405221"
---
# <a name="parallel"></a>parallel

Define una región paralela, que es código que se va a ejecutar varios subprocesos en paralelo.

## <a name="syntax"></a>Sintaxis

```
#pragma omp parallel [clauses]
{
   code_block
}
```

## <a name="arguments"></a>Argumentos

*Cláusula*<br/>
(Opcional) Cero o más cláusulas.  Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con **paralelo**.

## <a name="remarks"></a>Comentarios

El **paralelo** directiva es compatible con las cláusulas de OpenMP siguientes:

- [copyin](../../../parallel/openmp/reference/copyin.md)

- [default](../../../parallel/openmp/reference/default-openmp.md)

- [firstprivate](../../../parallel/openmp/reference/firstprivate.md)

- [if](../../../parallel/openmp/reference/if-openmp.md)

- [num_threads](../../../parallel/openmp/reference/num-threads.md)

- [private](../../../parallel/openmp/reference/private-openmp.md)

- [reduction](../../../parallel/openmp/reference/reduction.md)

- [Compartido](../../../parallel/openmp/reference/shared-openmp.md)

**paralelo** también se puede usar con el [secciones](../../../parallel/openmp/reference/sections-openmp.md) y [para](../../../parallel/openmp/reference/for-openmp.md) directivas.

Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo establecer el número de subprocesos y definir una región paralela. De forma predeterminada, el número de subprocesos es igual al número de procesadores lógicos en el equipo. Por ejemplo, si tiene un equipo con un procesador físico que tiene habilitado el hiperproceso, tendrá dos procesadores lógicos y, por lo tanto, dos subprocesos.

```
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="comment"></a>Comentario

Tenga en cuenta que el orden de salida puede variar en equipos diferentes.

## <a name="see-also"></a>Vea también

[Directivas](../../../parallel/openmp/reference/openmp-directives.md)