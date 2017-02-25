---
title: "Prioridad en las definiciones de macro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros, prioridad"
  - "NMAKE (programa), prioridad en definiciones de macro"
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Prioridad en las definiciones de macro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si una macro tiene varias definiciones, NMAKE utiliza la definición con mayor precedencia.  La lista siguiente muestra el orden de precedencia de mayor a menor:  
  
1.  Macro definida en la línea de comandos.  
  
2.  Macro definida en un archivo MAKE o en un archivo de inclusión.  
  
3.  Macro de variables de entorno heredada.  
  
4.  Macro definida en el archivo Tools.ini.  
  
5.  Macro predefinida, como [CC](../build/command-macros-and-options-macros.md) y [AS](../build/command-macros-and-options-macros.md).  
  
 Se ha de utilizar \/E para que las macros heredadas de variables de entorno reemplacen las macros de archivo MAKE con el mismo nombre.  Se ha de utilizar **\!UNDEF** para reemplazar una línea de comandos.  
  
## Vea también  
 [Definir una macro NMAKE](../build/defining-an-nmake-macro.md)