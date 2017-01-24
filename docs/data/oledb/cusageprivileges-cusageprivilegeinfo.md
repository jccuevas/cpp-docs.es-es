---
title: "CUsagePrivileges, CUsagePrivilegeInfo | Microsoft Docs"
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
  - "m_szObjectCatalog"
  - "CUsagePrivilegeInfo"
  - "m_bIsGrantable"
  - "OBJECT_NAME"
  - "m_szPrivilegeType"
  - "OBJECT_SCHEMA"
  - "IS_GRANTABLE"
  - "CUsagePrivileges"
  - "m_szGrantor"
  - "GRANTOR"
  - "GRANTEE"
  - "m_szObjectSchema"
  - "OBJECT_CATALOG"
  - "m_szObjectType"
  - "m_szObjectName"
  - "m_szGrantee"
  - "OBJECT_TYPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUsagePrivilegeInfo (clase de parámetro)"
  - "CUsagePrivileges (clase de definiciones de tipo)"
  - "GRANTEE"
  - "GRANTOR"
  - "IS_GRANTABLE"
  - "m_bIsGrantable"
  - "m_szGrantee"
  - "m_szGrantor"
  - "m_szObjectCatalog"
  - "m_szObjectName"
  - "m_szObjectSchema"
  - "m_szObjectType"
  - "m_szPrivilegeType"
  - "OBJECT_CATALOG"
  - "OBJECT_NAME"
  - "OBJECT_SCHEMA"
  - "OBJECT_TYPE"
ms.assetid: 09460e7f-3947-4837-ad1e-407b94acedb8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUsagePrivileges, CUsagePrivilegeInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CUsagePrivileges** typedef para implementar la clase **CUsagePrivilegeInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica los privilegios de USAGE en los objetos definidos en el catálogo al que esté disponible o concedido por un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas de USAGE\_PRIVILEGES](https://msdn.microsoft.com/en-us/library/ms722743.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szGrantor|GRANTOR|  
|m\_szGrantee|GRANTEE|  
|m\_szObjectCatalog|OBJECT\_CATALOG|  
|m\_szObjectSchema|OBJECT\_SCHEMA|  
|m\_szObjectName|OBJECT\_NAME|  
|m\_szObjectType|OBJECT\_TYPE|  
|m\_szPrivilegeType|PRIVILEGE\_TYPE|  
|m\_bIsGrantable|IS\_GRANTABLE|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)