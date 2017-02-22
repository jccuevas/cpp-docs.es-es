---
title: "Macros Null y no definidas | Microsoft Docs"
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
  - "macros, null y no definidas"
  - "NMAKE (programa), macros nulas"
  - "NMAKE (programa), macros sin definir"
  - "macros nulas en NMAKE"
  - "macros sin definir y NMAKE"
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Macros Null y no definidas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tanto las macros nulas como las no definidas se amplían a cadenas nulas, pero una macro definida como una cadena nula se considera definida en expresiones de preprocesamiento.  Para definir una macro como una cadena nula, no se han de especificar caracteres, excepto espacios o tabulaciones, a continuación del signo igual \(\=\) en una línea de comandos o en un archivo de comandos, y se ha de encerrar la definición o la cadena nula entre comillas \(" "\).  Para no definir una macro, se ha de utilizar **\!UNDEF**. Para obtener más información, vea [Directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md).  
  
## Vea también  
 [Definir una macro NMAKE](../build/defining-an-nmake-macro.md)