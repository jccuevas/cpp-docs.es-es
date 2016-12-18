---
title: "_crtDbgFlag | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_crtDbgFlag"
  - "crtDbgFlag"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_crtDbgFlag (constante)"
  - "crtDbgFlag (constante)"
  - "montón de depuración, marcas de control"
  - "montón de depuración, seguimiento de memoria en"
  - "habilitar marca de seguimiento de asignaciones de memoria"
  - "asignación de memoria, marca de seguimiento"
  - "memoria, seguimiento en el montón de depuración"
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _crtDbgFlag
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La marca **\_crtDbgFlag** consta de cinco campos de bits que controlan el modo en que las asignaciones de memoria en la versión de depuración del montón se siguen, comprueban, notifican y vuelcan.  Los campos de bits de la marca se establecen mediante la función [\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md).  Esta marca y sus campos de bits se declaran en Crtdbg.h.  Asimismo, esta marca solo está disponible cuando la marca [\_DEBUG](../c-runtime-library/debug.md) se ha definido en la aplicación.  
  
 Para más información sobre el uso de esta marca junto con otras funciones de depuración, vea [Funciones que indican el estado del montón](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions).  
  
## Vea también  
 [Marcas de control](../c-runtime-library/control-flags.md)