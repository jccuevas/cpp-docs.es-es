---
title: "CRestrictions::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRestrictions.Open"
  - "ATL::CRestrictions::Open"
  - "ATL.CRestrictions.Open"
  - "CRestrictions::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: 0aff0cc3-543a-47d2-8d6b-ebb36926b6db
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRestrictions::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un conjunto de resultados según las restricciones usuario\- proporcionadas.  
  
## Sintaxis  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCTSTR lpszParam 1 = NULL,  
   LPCTSTR lpszParam 2 = NULL,  
   LPCTSTR lpszParam 3 = NULL,  
   LPCTSTR lpszParam 4 = NULL,  
   LPCTSTR lpszParam 5 = NULL,  
   LPCTSTR lpszParam 6 = NULL,  
   LPCTSTR lpszParam 7 = NULL,  
   bool bBind = true  
);  
```  
  
#### Parámetros  
 `session`  
 \[in\] Especifica un objeto de sesión existente utilizado para conectarse al origen de datos.  
  
 *lpszParam*  
 \[in\] Especifica las restricciones del conjunto de filas de esquema.  
  
 `bBind`  
 \[in\] Especifica si enlazar la columna asignan automáticamente.  El valor predeterminado es **true**, que hace que la columna asignada para el enlace automáticamente.  El valor `bBind` a **false** evita el enlace automático de la columna asignada para poder enlazar manualmente. \(El enlace manual resulta especialmente interesante para los usuarios de OLAP\).  
  
## Valor devuelto  
 Uno de los valores estándar de `HRESULT` .  
  
## Comentarios  
 Puede especificar un máximo de siete restricciones en un conjunto de filas de esquema.  
  
 Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) para obtener información sobre restricciones definido en cada conjunto de filas de esquema.  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)