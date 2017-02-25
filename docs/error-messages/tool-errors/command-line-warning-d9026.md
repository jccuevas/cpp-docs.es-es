---
title: "Advertencia de la l&#237;nea de comandos D9026 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "D9026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "D9026"
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia de la l&#237;nea de comandos D9026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las opciones se aplican a toda la línea de comandos  
  
 Se ha especificado una opción en un comando después de especificar un nombre de archivo.  La opción se ha aplicado al archivo anterior.  
  
 Por ejemplo, en el comando  
  
```  
CL verdi.c /G5 puccini.c  
```  
  
 el archivo VERDI.c se compilará mediante la opción \/G5, no la opción predeterminada \/G4.  
  
 Este comportamiento es distinto de otras versiones anteriores que sólo aplicaban las opciones especificadas antes del nombre de archivo y, como consecuencia, compilaban VERDI.c mediante \/G4 y PUCCINI.c mediante \/G5.