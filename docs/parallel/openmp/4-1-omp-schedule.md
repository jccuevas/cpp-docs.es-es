---
title: "4.1 OMP_SCHEDULE | Microsoft Docs"
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
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.1 OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_SCHEDULE** sólo se aplica a **Para** y las directivas de **paralelo para** que tienen la programación escriben **Motor en tiempo de ejecución**.  El tipo de programación y el tamaño del fragmento para todos estos bucles pueden establecer en tiempo de ejecución estableciendo esta variable de entorno a los tipos reconocidos cualquiera de programación y un opcional *chunk\_size*.  
  
 For **for** and **parallel for** directives that have a schedule type other than **runtime**, **OMP\_SCHEDULE** is ignored.  El valor predeterminado para esta variable de entorno se implementación\-definido.  Si se establece el opcionales *chunk\_size* , el valor deben ser positivos.  Si *chunk\_size* no está establecida, el valor 1 se supone, a menos que en el caso de una programación de **Estática** .  Para una programación de **Estática** , el tamaño predeterminado del fragmento se establece en el espacio de iteración del bucle dividido por el número de subprocesos aplicado al bucle.  
  
 Ejemplo:  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## referencias cruzadas:  
  
-   La directiva de**Para** , vea [sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en la página 11.  
  
-   la directiva de**paralelo para** , vea [sección 2.5.1](../Topic/2.5.1%20parallel%20for%20Construct.md) en la página 16.