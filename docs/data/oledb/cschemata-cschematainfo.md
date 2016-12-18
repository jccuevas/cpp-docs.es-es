---
title: "CSchemata, CSchemataInfo | Microsoft Docs"
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
  - "DEFAULT_CHARACTER_SET_CATALOG"
  - "DEFAULT_CHARACTER_SET_SCHEMA"
  - "m_szCharName"
  - "CSchemataInfo"
  - "m_szCatalog"
  - "m_szCharCatalog"
  - "m_szOwner"
  - "m_szCharSchema"
  - "CSchemata"
  - "m_szName"
  - "DEFAULT_CHARACTER_SET_NAME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSchemata (clase de definiciones de tipo)"
  - "CSchemataInfo (clase de parámetro)"
  - "DEFAULT_CHARACTER_SET_CATALOG"
  - "DEFAULT_CHARACTER_SET_NAME"
  - "DEFAULT_CHARACTER_SET_SCHEMA"
  - "m_szCatalog"
  - "m_szCharCatalog"
  - "m_szCharName"
  - "m_szCharSchema"
  - "m_szName"
  - "m_szOwner"
ms.assetid: 9d06d65a-c27b-446d-bc42-c7e487b0d9c5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSchemata, CSchemataInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CSchemata** typedef para implementar la clase **CSchemataInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica los esquemas que pertenecen a un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas de los ESQUEMAS](https://msdn.microsoft.com/en-us/library/ms716887.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szCatalog|CATALOG\_NAME|  
|m\_szName|SCHEMA\_NAME|  
|m\_szOwner|SCHEMA\_OWNER|  
|m\_szCharCatalog|DEFAULT\_CHARACTER\_SET\_CATALOG|  
|m\_szCharSchema|DEFAULT\_CHARACTER\_SET\_SCHEMA|  
|m\_szCharName|DEFAULT\_CHARACTER\_SET\_NAME|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)