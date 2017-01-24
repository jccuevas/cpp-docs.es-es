---
title: "OpenMP Libraries | Microsoft Docs"
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
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Libraries
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Describe los archivos .lib que constituyen las bibliotecas en tiempo de ejecución de OpenMP en Visual C\+\+.  
  
 Las bibliotecas siguientes contienen funciones de la biblioteca en tiempo de ejecución de Visual C\+\+ OpenMP.  
  
|biblioteca en tiempo de ejecución de OpenMP|Características|  
|-------------------------------------------------|---------------------|  
|VCOMP.LIB|Multiproceso, vínculo dinámico \(biblioteca de importación para VCOMP.LIB\).|  
|VCOMPD.LIB|Multiproceso, vínculo dinámico \(biblioteca de importación para VCOMPD.LID\) \(depuración\)|  
  
 Si el \_DEBUG se define en una compilación y si `#include omp.h` está en código fuente, VCOMPD.LIB se biblioteca predeterminada.  Si no, VCOMP.LIB se utilizará.  
  
 Puede utilizar [\/NODEFAULTLIB \(Omitir bibliotecas\)](../../../build/reference/nodefaultlib-ignore-libraries.md) para quitar biblioteca y explícitamente el vínculo predeterminados con lib de la opción.  
  
 Los archivos DLL de OpenMP están en el directorio redistribuible de Visual C\+\+ y deben distribuirse con las aplicaciones que usan OpenMP.  
  
## Vea también  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)