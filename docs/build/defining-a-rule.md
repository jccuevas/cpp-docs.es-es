---
title: "Definir una regla | Microsoft Docs"
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
  - "definir reglas de inferencia"
  - "NMAKE (programa), reglas de inferencia"
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Definir una regla
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El argumento *fromext* representa la extensión de un archivo dependiente, y el argumento *toext* representa la extensión de un archivo de destino.  
  
```  
.fromext.toext:  
   commands  
```  
  
## Comentarios  
 Las extensiones no distinguen entre mayúsculas y minúsculas.  Se puede llamar a las macros para representar *fromext* y *toext*; las macros se amplían durante el preprocesamiento.  El punto \(.\) que precede a *fromext* debe estar al principio de la línea.  El signo de dos puntos \(:\) puede ir precedido de varios espacios o tabulaciones o de ninguno.  Puede ir seguido sólo de espacios o tabulaciones, un punto y coma \(;\) para especificar un comando, un signo de número \(\#\) para especificar un comentario, o un carácter de nueva línea.  No se permiten otros espacios.  Los comandos se especifican igual que en los bloques de descripción.  
  
## ¿Sobre qué desea obtener más información?  
 [Rutas de búsqueda en reglas](../build/search-paths-in-rules.md)  
  
## Vea también  
 [Reglas de inferencia](../build/inference-rules.md)