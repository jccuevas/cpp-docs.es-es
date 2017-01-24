---
title: "system (Funci&#243;n) | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "función de sistema"
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# system (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.10.4.5** Contenido y modo de ejecución de la cadena por la función **system**  
  
 La función **system** ejecuta un comando interno del sistema operativo, o un archivo .EXE, .COM \(.CMD en Windows NT\) o .BAT dentro de un programa de C, en lugar de la línea de comandos.  
  
 La función system encuentra el intérprete de comandos, que es normalmente CMD.EXE en el sistema operativo Windows NT o COMMAND.COM en Windows.  Después, la función system pasa la cadena del argumento al intérprete de comandos.  
  
 Para obtener más información, vea [system, \_wsystem](../c-runtime-library/reference/system-wsystem.md).  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)