---
title: "END_ACCESSOR_MAP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "END_ACCESSOR_MAP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "END_ACCESSOR_MAP (macro)"
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# END_ACCESSOR_MAP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el final de las entradas del mapa del descriptor.  
  
## Sintaxis  
  
```  
  
END_ACCESSOR_MAP( )  
  
```  
  
## Comentarios  
 Para múltiples descriptores de acceso en un conjunto de filas, debe especificar `BEGIN_ACCESSOR_MAP` y utilizar la macro de `BEGIN_ACCESSOR` para cada descriptor de acceso individual.  La macro de `BEGIN_ACCESSOR` se completa con la macro de `END_ACCESSOR` .  La macro de `BEGIN_ACCESSOR_MAP` se completa con la macro de `END_ACCESSOR_MAP` .  
  
## Ejemplo  
 Vea [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN\_ACCESSOR\_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md)