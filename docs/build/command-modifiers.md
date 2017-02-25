---
title: "Modificadores de comandos | Microsoft Docs"
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
  - "modificadores de comandos"
  - "NMAKE (programa), modificadores de comandos"
ms.assetid: b661c432-210f-4f05-bc56-744a46e0fc0b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Modificadores de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se pueden especificar uno o varios modificadores de comandos precediendo a un comando, separado opcionalmente por espacios o tabulaciones.  Al igual que sucede con los comandos, se debe aplicar sangría a los modificadores.  
  
|Modificador|Objetivo|  
|-----------------|--------------|  
|@*comando*|Evita que se muestre el comando.  No se suprime la presentación mediante comandos.  De forma predeterminada, NMAKE repite todos los comandos ejecutados.  Se ha de utilizar \/S para suprimir la presentación de la totalidad del archivo MAKE y **.SILENT** para suprimir la presentación de una parte del archivo MAKE.|  
|**–**\[`number` \]*command*|Desactiva la comprobación de errores para *command*.  De forma predeterminada, NMAKE se detiene si un comando devuelve un código de salida distinto de cero.  Si se utiliza –`number`, NMAKE se detiene si el código de salida supera el valor de `number`.  No puede haber espacios ni tabulaciones entre el guión y *number.* Debe haber al menos un espacio o una tabulación entre `number` y *command*.  Se ha de utilizar \/I para desactivar la comprobación de errores para la totalidad del archivo MAKE e **.IGNORE** para desactivar la comprobación de errores para una parte del archivo MAKE.|  
|**\!** *comando*|Ejecuta *command* para cada archivo dependiente si *command* utiliza **$\*\*** \(todos los archivos dependientes existentes en la dependencia\) o **$?**. \(todos los archivos dependientes existentes en la dependencia con una marca de tiempo posterior al destino\).|  
  
## Vea también  
 [Comandos en un archivo MAKE](../build/commands-in-a-makefile.md)