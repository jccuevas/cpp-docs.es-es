---
title: "Advertencia de la l&#237;nea de comandos D9027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9027"
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia de la l&#237;nea de comandos D9027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nombre '\<del archivo de\>' código fuente omitido  
  
 CL.exe ha omitido el archivo de código fuente de entrada.  
  
 Esta advertencia puede deberse a la existencia de un espacio entre la opción \/Fo y un nombre de archivo de salida en una línea de comandos con la opción \/c.  Por ejemplo:  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Dado que hay un espacio entre \/Fo y `output.obj,` CL.exe toma `output.obj` como el nombre del archivo de entrada.  Para solucionar este problema, quite el espacio:  
  
```  
cl /c /Fooutput.obj input.c   
```