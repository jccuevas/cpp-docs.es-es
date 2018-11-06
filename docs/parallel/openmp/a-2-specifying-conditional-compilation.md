---
title: A.2 Especificar una compilación condicional
ms.date: 11/04/2016
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
ms.openlocfilehash: 92ae22ffac1b1a1c3fc45a9a7a883203ff6d251e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491226"
---
# <a name="a2---specifying-conditional-compilation"></a>A.2 Especificar una compilación condicional

Los siguientes ejemplos ilustran el uso de la compilación condicional mediante la macro OpenMP `_OPENMP` ([sección 2.2](../../parallel/openmp/2-2-conditional-compilation.md) página 8). Con la compilación de OpenMP, el `_OPENMP` macro queda definida.

```
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

El operador de preprocesador definido permite más de una macro que probarse en una sola directiva.

```
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```