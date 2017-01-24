---
title: "Reglas de inferencia | Microsoft Docs"
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
  - "reglas de inferencia en NMAKE"
  - "NMAKE (programa), reglas de inferencia"
  - "reglas, inferencia"
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Reglas de inferencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las reglas de inferencia proporcionan comandos para actualizar destinos e inferir dependientes para destinos.  Las extensiones en una regla de inferencia coinciden con un destino y dependiente únicos que tienen el mismo nombre base.  Las reglas de inferencia son definidas por el usuario o predefinidas; las reglas predefinidas se pueden volver a definir.  
  
 Si una dependencia no actualizada no tiene comandos, y si [.SUFFIXES](../build/dot-directives.md) contiene la extensión del dependiente, NMAKE usa una regla cuyas extensiones coinciden con el destino y un archivo existente en el directorio actual o especificado.  Si más de una regla coincide con archivos existentes, la lista **.SUFFIXES** determina cuál se ha de usar; la prioridad de la lista desciende de izquierda a derecha.  Si no existe un archivo dependiente y no está listado como un destino en otro bloque de descripción, una regla de inferencia puede crear el dependiente que falta a partir de otro archivo con el mismo nombre base.  Si el destino de un bloque de descripción no tiene dependientes ni comandos, una regla de inferencia puede actualizar el destino.  Las reglas de inferencia pueden compilar un destino de línea de comandos aunque no exista ningún bloque de descripción.  NMAKE puede llamar a una regla para un dependiente inferido aunque se especifique un dependiente explícito.  
  
## ¿Sobre qué desea obtener más información?  
 [Definir una regla](../build/defining-a-rule.md)  
  
 [Reglas de modo por lotes](../build/batch-mode-rules.md)  
  
 [Reglas predefinidas](../build/predefined-rules.md)  
  
 [Dependientes inferidos y reglas](../build/inferred-dependents-and-rules.md)  
  
 [La precedencia en las reglas de inferencia](../build/precedence-in-inference-rules.md)  
  
## Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)