---
title: "END_ACCESSOR | Microsoft Docs"
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
  - "END_ACCESSOR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "END_ACCESSOR (macro)"
ms.assetid: 26f74167-68c4-4909-a474-73dc7ebc9542
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# END_ACCESSOR
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marca el final de una entrada de descriptor de acceso.  
  
## Sintaxis  
  
```  
  
END_ACCESSOR( )  
  
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
 [END\_ACCESSOR\_MAP](../../data/oledb/end-accessor-map.md)