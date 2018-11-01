---
title: A.2 especificar una compilación condicional | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d8b0f3df67313dbf03d40077a551fe64930199d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393703"
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