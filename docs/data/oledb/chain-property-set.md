---
title: "CHAIN_PROPERTY_SET | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHAIN_PROPERTY_SET"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHAIN_PROPERTY_SET (macro)"
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CHAIN_PROPERTY_SET
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Grupos de esta de la macro propiedad strings junto.  
  
## Sintaxis  
  
```  
  
CHAIN_PROPERTY_SET(  
ChainClass   
)  
  
```  
  
#### Parámetros  
 *ChainClass*  
 \[in\] El nombre de la clase para encadenar las propiedades para.  Esta es una clase generada por el asistente para proyectos ATL que ya contiene un mapa \(como una sesión, un comando, o una clase de objeto de origen de datos\).  
  
## Comentarios  
 Puede encadenar una propiedad establecida de otra clase a dispone de la clase, se tiene acceso a las propiedades directamente de la clase.  
  
> [!CAUTION]
>  Use esta macro con moderación.  El uso incorrecto puede hacer un consumidor un error en las pruebas de conformidad de OLE DB.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)