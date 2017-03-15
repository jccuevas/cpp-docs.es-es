---
title: "Error de las herramientas del vinculador LNK1106 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1106"
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1106
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo no válido o disco lleno: no se puede buscar en location  
  
 La herramienta no pudo leer ni escribir en `location` en un archivo asignado en memoria.  
  
### Posibles causas del error:  
  
1.  Disco lleno.  
  
     Libere algo de espacio y vuelva a realizar la vinculación.  
  
2.  Se está intentando realizar la vinculación a través de la red.  
  
     Algunas redes no admiten por entero los archivos asignados en memoria que utiliza el vinculador.  Intente realizar la vinculación en su disco local.  
  
3.  Bloque defectuoso en el disco.  
  
     Si bien el sistema operativo y el hardware de disco deberían haber detectado cualquier error, puede resultar conveniente ejecutar un programa de comprobación del disco.  
  
4.  El espacio en el montón es insuficiente  
  
     Para obtener más información, vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md).