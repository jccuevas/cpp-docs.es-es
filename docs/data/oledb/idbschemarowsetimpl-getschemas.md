---
title: "IDBSchemaRowsetImpl::GetSchemas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBSchemaRowsetImpl::GetSchemas"
  - "GetSchemas"
  - "IDBSchemaRowsetImpl<SessionClass>::GetSchemas"
  - "ATL.IDBSchemaRowsetImpl.GetSchemas"
  - "ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas"
  - "IDBSchemaRowsetImpl.GetSchemas"
  - "IDBSchemaRowsetImpl::GetSchemas"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetSchemas (método)"
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBSchemaRowsetImpl::GetSchemas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve una lista de conjuntos de filas de esquema accesibles por [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
## Sintaxis  
  
```  
  
STDMETHOD  
( GetSchema s )(  
   ULONG *   
pcSchemas  
,  
   GUID **   
prgSchemas  
,  
   ULONG**   
prgRest  
);  
  
```  
  
#### Parámetros  
 *pcSchemas*  
 \[out\] Puntero a un **ULONG** que se rellena con el número de esquemas.  
  
 *prgSchemas*  
 \[out\] Puntero a una matriz de GUID que se rellena con un puntero a una matriz de GUID de conjuntos de filas de esquema.  
  
 *prgRest*  
 \[out\] Puntero a una matriz de **ULONG** que se va a rellenar con la matriz de restricciones.  
  
## Comentarios  
 Este método devuelve una matriz de todos los conjuntos de filas de esquema admitidos por el proveedor. Consulte [IDBSchemaRowset:: GetSchemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 La implementación de esta función exige que el usuario tenga una asignación de esquema en la clase de sesión. Luego, con la información de la asignación de esquema, responde con la matriz de GUID de los esquemas de la asignación. Representa los esquemas admitidos por el proveedor.  
  
## Requisitos  
 **Encabezado:** atldb.h  
  
## Vea también  
 [IDBSchemaRowsetImpl \(Clase\)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [IDBSchemaRowsetImpl Class Members](http://msdn.microsoft.com/es-es/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [IDBSchemaRowset:: GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)