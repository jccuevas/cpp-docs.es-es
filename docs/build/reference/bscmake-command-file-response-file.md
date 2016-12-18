---
title: "Archivo de comandos de BSCMAKE (Archivo de respuesta) | Microsoft Docs"
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
helpviewer_keywords: 
  - "BSCMAKE, archivo de comandos"
  - "BSCMAKE, archivo de respuesta"
  - "archivos de comandos"
  - "archivos de comandos, BSCMAKE"
  - "archivos de respuesta"
  - "archivos de respuesta, BSCMAKE"
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivo de comandos de BSCMAKE (Archivo de respuesta)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede proporcionar una parte o la totalidad de la entrada de la línea de comandos en un archivo de comandos.  Especifique el archivo de comandos con la siguiente sintaxis:  
  
```  
BSCMAKE @filename  
```  
  
 Sólo se permite un archivo de comandos.  Se puede especificar una ruta de acceso con el campo *filename*.  El campo *filename va precedido de un signo arroba* \(@\).  BSCMAKE no supone una extensión.  Se pueden especificar campos *sbrfiles* adicionales en la línea de comandos después del campo *filename*.  El archivo de comandos es un archivo de texto que contiene la entrada para BSCMAKE en el mismo orden en que se especificaría en la línea de comandos.  Separe los argumentos de la línea de comandos con uno o varios espacios, tabulaciones o caracteres de nueva línea.  
  
 El comando siguiente llama a BSCMAKE usando un archivo de comandos:  
  
```  
BSCMAKE @prog1.txt  
```  
  
 A continuación se muestra un archivo de comandos de ejemplo:  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## Vea también  
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)