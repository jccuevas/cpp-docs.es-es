---
title: "Dependientes inferidos | Microsoft Docs"
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
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Dependientes inferidos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que los dependientes explícitos.  Si un dependiente inferido no está actualizado con respecto a su destino, NMAKE invoca el bloque de comandos para la dependencia.  Si no existe un dependiente inferido o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido.  Para obtener más información sobre dependientes inferidos, vea [Reglas de inferencia](../build/inference-rules.md).  
  
## Vea también  
 [Dependientes](../build/dependents.md)