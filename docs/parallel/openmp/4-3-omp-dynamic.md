---
title: 4.3 OMP_DYNAMIC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f376fe639d9bca58b6e2bd55fd081b88921a7342
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC
El **OMP_DYNAMIC** variable de entorno habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones en paralelo, a menos que realizar un ajuste dinámico explícitamente está habilitado o deshabilitado mediante una llamada a la **omp_set_dynamic ()** rutina de biblioteca. Su valor debe ser **TRUE** o **FALSE**.  
  
 Si establece en **TRUE**, el número de subprocesos que se usan para ejecutar regiones en paralelo puede ser ajustado por el entorno en tiempo de ejecución para utilizar mejor los recursos del sistema.  Si establece en **FALSE**, realizar un ajuste dinámico está deshabilitado. La condición predeterminada es definido por la implementación.  
  
 Ejemplo:  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   Para obtener más información sobre las regiones en paralelo, vea [sección 2.3](../../parallel/openmp/2-3-parallel-construct.md) en página 8.  
  
-   **omp_set_dynamic ()** función, vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en página 39.