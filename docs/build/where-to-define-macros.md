---
title: "D&#243;nde definir macros | Microsoft Docs"
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
  - "definir macros"
  - "macros, NMAKE"
  - "NMAKE (programa), definir macros"
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# D&#243;nde definir macros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros se definen en líneas de comandos, archivos de comandos, un archivo MAKE o el archivo Tools.ini.  
  
 En un archivo MAKE o en el archivo Tools.ini, cada definición de macro debe aparecer en una línea independiente y no puede empezar por un espacio o una tabulación.  Los espacios o tabulaciones a ambos lados del signo igual se omiten.  Todos los [caracteres de cadena](../build/defining-an-nmake-macro.md) son literales, incluidas las comillas tipográficas y los espacios incrustados.  
  
 En una línea de comandos o en un archivo de comandos, los espacios y las tabulaciones delimitan argumentos y no pueden estar delante ni detrás del signo igual.  Si `string` tiene tabulaciones o espacios incrustados, la propia cadena o la macro completa se ha de encerrar entre comillas \(" "\).  
  
## Vea también  
 [Definir una macro NMAKE](../build/defining-an-nmake-macro.md)