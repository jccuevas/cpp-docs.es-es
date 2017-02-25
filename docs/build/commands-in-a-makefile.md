---
title: "Comandos en un archivo MAKE | Microsoft Docs"
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
  - "comandos, Make (archivos)"
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Comandos en un archivo MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un bloque de descripción o una regla de inferencia especifica la ejecución de un bloque de comandos si la dependencia no está actualizada.  NMAKE muestra cada comando antes de ejecutarlo, a menos que se utilice \/S, **.SILENT**, **\!CMDSWITCHES** o @.  NMAKE busca una regla de inferencia coincidente si un bloque de descripción no va seguido de un bloque de comandos.  
  
 Un bloque de comandos contiene uno o varios comandos, cada uno en su propia línea.  No puede haber una línea en blanco entre la dependencia o la regla y el bloque de comandos.  Sin embargo, puede haber una línea que sólo tenga espacios o tabulaciones; esta línea se interpreta como un comando nulo y no se produce ningún error.  Se permiten líneas en blanco entre líneas de comandos.  
  
 Una línea de comandos empieza por uno o varios espacios o tabulaciones.  Una barra inversa \(\\\) seguida de un carácter de nueva línea se interpreta como un espacio en el comando; se ha de utilizar una barra inversa al final de una línea para continuar un comando en la línea siguiente.  NMAKE interpreta la barra inversa literalmente si a continuación de ella hay otro carácter, incluido un espacio o una tabulación.  
  
 Un comando precedido de un punto y coma \(;\) puede aparecer en una línea de dependencia o en una regla de inferencia, independientemente de que le siga o no un bloque de comandos:  
  
```  
project.obj : project.c project.h ; cl /c project.c  
```  
  
## ¿Sobre qué desea obtener más información?  
 [Modificadores de comandos](../build/command-modifiers.md)  
  
 [Sintaxis de las partes de un nombre de archivo](../build/filename-parts-syntax.md)  
  
 [Archivos en línea en un archivo MAKE](../build/inline-files-in-a-makefile.md)  
  
## Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)