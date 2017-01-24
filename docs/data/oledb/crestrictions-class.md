---
title: "CRestrictions (Clase) | Microsoft Docs"
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
  - "ATL::CRestrictions"
  - "CRestrictions"
  - "ATL.CRestrictions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRestrictions (clase)"
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRestrictions (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase genérica que permite especificar las restricciones de conjuntos de filas de esquema.  
  
## Sintaxis  
  
```  
template <   
   class T,   
   short nRestrictions,   
   const GUID* pguid   
>  
class CRestrictions : public CSchemaRowset <   
   T,   
   nRestrictions   
>  
```  
  
#### Parámetros  
 `T`  
 La clase utilizada para el descriptor de acceso.  
  
 `nRestrictions`  
 El número de columnas de restricción del conjunto de filas de esquema.  
  
 `pguid`  
 Un puntero al GUID del esquema.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Abrir](../../data/oledb/crestrictions-open.md)|Devuelve un conjunto de resultados según las restricciones usuario\- proporcionadas.|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)