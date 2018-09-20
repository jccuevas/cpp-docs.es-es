---
title: 4.1 OMP_SCHEDULE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cbdad5ab56ea6979ae2b5952b092b5e85c7bdfa8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433457"
---
# <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

**OMP_SCHEDULE** solo se aplica a **para** y **paralelas para** directivas que tienen el tipo de programación **en tiempo de ejecución**. Se puede establecer el tamaño de tipo y el fragmento de programación para todos los bucles de este tipo en tiempo de ejecución al establecer esta variable de entorno para cualquiera de los tipos de programación reconocido y opcional *chunk_size*.

Para **para** y **paralelas para** directivas que tienen un tipo de programación distinto **en tiempo de ejecución**, **OMP_SCHEDULE** se omite. El valor predeterminado de esta variable de entorno es definido por la implementación. Si el elemento opcional *chunk_size* se establece, el valor debe ser positivo. Si *chunk_size* no está establecido, se supone que un valor de 1, excepto en el caso de un **estático** programación. Para un **estático** programación, el tamaño del fragmento predeterminado se establece en el espacio de iteración del bucle dividido por el número de subprocesos que se aplica al bucle.

Ejemplo:

```
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

## <a name="cross-references"></a>Referencias cruzadas:

- **para** la directiva, consulte [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11.

- **paralelo para** la directiva, consulte [sección 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) en la página 16.