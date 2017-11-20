---
title: 'IDBSchemaRowsetImpl:: GetSchemas | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
dev_langs: C++
helpviewer_keywords: GetSchemas method
ms.assetid: fbe725a6-3acd-45f8-bcaf-10a6c1239cd2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 20d346ff4b2ed3dd3f4fc90190c51e1fa41dbc46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="idbschemarowsetimplgetschemas"></a>IDBSchemaRowsetImpl::GetSchemas
Devuelve una lista de conjuntos de filas de esquema accesibles por [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      STDMETHOD ( GetSchema s )(  
   ULONG * pcSchemas,  
   GUID ** prgSchemas,  
   ULONG** prgRest  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pcSchemas*  
 [out] Puntero a un **ULONG** que se rellena con el número de esquemas.  
  
 *prgSchemas*  
 [out] Puntero a una matriz de GUID que se rellena con un puntero a una matriz de GUID de conjuntos de filas de esquema.  
  
 *prgRest*  
 [out] Puntero a una matriz de **ULONG**que se va a rellenar con la matriz de restricciones.  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve una matriz de todos los conjuntos de filas de esquema admitidos por el proveedor. Vea [IDBSchemaRowset:: GetSchemas](https://msdn.microsoft.com/en-us/library/ms719605.aspx) en el SDK de Windows.  
  
 La implementación de esta función exige que el usuario tenga una asignación de esquema en la clase de sesión. Luego, con la información de la asignación de esquema, responde con la matriz de GUID de los esquemas de la asignación. Representa los esquemas admitidos por el proveedor.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (clase)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl:: GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)   
 [IDBSchemaRowset:: GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)