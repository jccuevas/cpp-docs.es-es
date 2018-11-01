---
title: 2.2 Compilación condicional
ms.date: 11/04/2016
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
ms.openlocfilehash: 9dc107ee9e5328df205d4b6f826f71c23abfb3ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658554"
---
# <a name="22-conditional-compilation"></a>2.2 Compilación condicional

El _**OPENMP** nombre de macro se define mediante implementaciones compatibles con OpenMP como la constante decimal *AAAAMM*, que será el año y mes de la especificación aprobada. Esta macro no debe ser el sujeto de un **#define** o un **#undef** preprocesamiento de directiva.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si los proveedores de definan extensiones para OpenMP, pueden especificar adicionales macros predefinidas.