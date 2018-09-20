---
title: 2.2 compilación condicional | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440386"
---
# <a name="22-conditional-compilation"></a>2.2 Compilación condicional

El _**OPENMP** nombre de macro se define mediante implementaciones compatibles con OpenMP como la constante decimal *AAAAMM*, que será el año y mes de la especificación aprobada. Esta macro no debe ser el sujeto de un **#define** o un **#undef** preprocesamiento de directiva.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si los proveedores de definan extensiones para OpenMP, pueden especificar adicionales macros predefinidas.