---
title: 4.3 OMP_DYNAMIC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 103067b28990854fb6522c19f4349a9607d65bab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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