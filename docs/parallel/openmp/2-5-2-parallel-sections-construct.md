---
title: 2.5.2 parallel secciones construcción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 073d0561fe4bfbb96ed88681a077da6fc985c963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402335"
---
# <a name="252-parallel-sections-construct"></a>2.5.2 parallel sections (Construcción)

El **secciones en paralelo** directiva proporciona un formulario de método abreviado para especificar un **paralelo** región que contiene una sola **secciones** directiva. La semántica es idéntica a la especificación explícita de un **paralelo** directiva seguido inmediatamente por un **secciones** directiva. La sintaxis de la **secciones en paralelo** directiva es como sigue:

```
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

El *cláusula* puede ser una de las cláusulas aceptadas por el **paralelo** y **secciones** directivas, excepto el **nowait** cláusula.

## <a name="cross-references"></a>Referencias cruzadas:

- **paralelo** la directiva, consulte [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) página 8.

- **las secciones** la directiva, consulte [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14.