---
title: "4. Environment Variables | Microsoft Docs"
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
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4. Environment Variables
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este capítulo describe las variables de entorno de OpenMP c y C\+\+ API \(o los mecanismos específicos de la plataforma equivalentes\) que controlan la ejecución de código paralelo.  Los nombres de variables de entorno deben estar en mayúsculas.  Los valores asignados a ellas no distinguen entre mayúsculas y minúsculas y pueden tener espacio en blanco inicial y final.  Las modificaciones en los valores después de programa han iniciado se omiten.  
  
 Las variables de entorno son los siguientes:  
  
-   **OMP\_SCHEDULE** establece el tipo de programación en tiempo de ejecución y el tamaño del fragmento.  
  
-   **OMP\_NUM\_THREADS** establece el número de subprocesos que se utilizarán durante la ejecución.  
  
-   Los permisos de**OMP\_DYNAMIC** o deshabilita el ajuste dinámico de subprocesos.  
  
-   Los permisos de**OMP\_NESTED** o deshabilita paralelismo anidados.  
  
 Los ejemplos de este capítulo muestran solo cómo estas variables se pueden establecer en entornos del shell de UNIX C \(csh\).  En el shell de Korn y entornos de DOS acciones son similares, como sigue:  
  
 csh:  
 setenv OMP\_SCHEDULE “dynamic”  
  
 ksh:  
 exportación OMP\_SCHEDULE\= " dynamic”  
  
 DOS:  
 establezca OMP\_SCHEDULE\= " dynamic”