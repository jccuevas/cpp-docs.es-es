---
title: IDBSchemaRowsetImpl::GetRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
dev_langs:
- C++
helpviewer_keywords:
- GetRowset method
ms.assetid: 3ae28c22-e186-4a15-8591-b0192e784a6f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 143bec7cf78f039ccb4cad69c154764608376693
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="idbschemarowsetimplgetrowset"></a>IDBSchemaRowsetImpl::GetRowset
Devuelve un conjunto de filas de esquema.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetRowset)(IUnknown *pUnkOuter,  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown **ppRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Valor **IUnknown** exterior al agregar; en caso contrario, **NULL**.  
  
 `rguidSchema`  
 [in] Referencia al GUID del conjunto de filas de esquema solicitado (por ejemplo, `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Recuento de restricciones que se aplicarán al conjunto de filas.  
  
 `rgRestrictions`  
 [in] Matriz de `cRestrictions`**cRestrictions**que representa las restricciones.  
  
 `riid`  
 [in] IID que se va a solicitar del conjunto de filas de esquema recién creado.  
  
 `cPropertySets`  
 [in] Número de conjuntos de propiedad que se van a establecer.  
  
 `rgPropertySets`  
 [in/out] Matriz de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que se van a establecer en el conjunto de filas de esquema recién creado.  
  
 `ppRowset`  
 [out] Puntero a la interfaz solicitada en el conjunto de filas de esquema recién creado.  
  
## <a name="remarks"></a>Comentarios  
 Este método exige que el usuario tenga una asignación de esquema en la clase de sesión. Mediante la información de la asignación de esquema, `GetRowset` crea un objeto de conjunto de filas determinado si el parámetro `rguidSchema` es igual a uno de los GUID de las entradas de asignación. Vea [SCHEMA_ENTRY](../../data/oledb/schema-entry.md) para obtener una descripción de la entrada de asignación.  
  
 Vea [IDBSchemaRowset:: GetRowset](https://msdn.microsoft.com/en-us/library/ms722634.aspx) en el SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (clase)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [IDBSchemaRowsetImpl::GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)