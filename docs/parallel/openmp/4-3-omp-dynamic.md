---
title: "4.3 OMP_DYNAMIC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a15edefb-1f85-4f06-a427-beb3cfc4434f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.3 OMP_DYNAMIC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La variable de entorno **OMP\_DYNAMIC** habilita o deshabilita el ajuste dinámico de subprocesos disponibles para la ejecución de las regiones paralelas a menos que el ajuste dinámico explícitamente esté habilitado o deshabilitado llamando a la rutina de biblioteca de **omp\_set\_dynamic** .  El valor debe ser **TRUE** o **FALSO**.  
  
 Si se establece en **TRUE**, el número de subprocesos que se utilizan para ejecutar las regiones paralelas se puede ajustar el entorno en tiempo de ejecución el mejor utiliza recursos del sistema.  Si deshabilita el conjunto a **FALSO**, ajuste dinámico.  la condición predeterminada es implementación\-definido.  
  
 Ejemplo:  
  
```  
setenv OMP_DYNAMIC TRUE  
```  
  
## referencias cruzadas:  
  
-   Para obtener más información sobre las regiones paralelas, vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.  
  
-   la función de**omp\_set\_dynamic** , vea [sección 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) en la página 39.