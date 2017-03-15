---
title: "Dependientes inferidos y reglas | Microsoft Docs"
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
  - "dependientes, inferidas"
  - "dependientes inferidos en NMAKE"
  - "reglas inferidas en NMAKE"
  - "reglas, inferidas"
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Dependientes inferidos y reglas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE supone un dependiente inferido para un destino si existe una regla de inferencia aplicable.  Una regla se aplica si:  
  
-   *toext* coincide con la extensión del destino.  
  
-   *fromext* coincide con la extensión de un archivo que tiene el nombre base del destino y que existe en el directorio actual o especificado.  
  
-   *fromext* está en [.SUFFIXES](../build/dot-directives.md); ningún otro argumento *fromext* de una regla coincidente tiene una prioridad .**SUFFIXES** superior.  
  
-   Ningún dependiente explícito tiene una prioridad .**SUFFIXES superior.**  
  
 Los dependientes inferidos pueden provocar efectos secundarios inesperados.  Si el bloque de descripción del destino contiene comandos, NMAKE ejecuta esos comandos en lugar de los comandos de la regla.  
  
## Vea también  
 [Reglas de inferencia](../build/inference-rules.md)