---
title: IDBSchemaRowsetImpl::CreateSchemaRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
dev_langs:
- C++
helpviewer_keywords:
- CreateSchemaRowset method
ms.assetid: ad3e3e4d-45b9-461c-b7b8-3af6843631b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e819805f9c73b2f8622b21b999b0db5f6771ecbe
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="idbschemarowsetimplcreateschemarowset"></a>IDBSchemaRowsetImpl::CreateSchemaRowset
Implementa una función de creación de objetos COM para el objeto especificado por el parámetro de la plantilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
template template <class SchemaRowsetClass>  
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[],  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   SchemaRowsetClass*& pSchemaRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pUnkOuter`  
 [in] Valor [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) externo al agregar; en caso contrario, **NULL**.  
  
 `cRestrictions`  
 [in] El recuento de restricciones aplicado al conjunto de filas de esquema.  
  
 `rgRestrictions`  
 [in] Una matriz de `cRestrictions`**VARIANT**se aplicará al conjunto de filas.  
  
 `riid`  
 [in] La interfaz para [QueryInterface](../../atl/queryinterface.md) en el valor **IUnknown**de salida.  
  
 `cPropertySets`  
 [in] Número de conjuntos de propiedad que se van a establecer.  
  
 `rgPropertySets`  
 [in] Una matriz de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que especifica las propiedades que se están estableciendo.  
  
 `ppRowset`  
 [out] El valor **IUnknown** saliente solicitado por `riid`. Este valor **IUnknown** es una interfaz en el objeto de conjunto de filas de esquema.  
  
 `pSchemaRowset`  
 [out] Un puntero a una instancia de la clase de conjunto de filas de esquema. Normalmente, este parámetro no se usa, pero se puede usar si debe realizar más trabajo en el conjunto de filas de esquema antes de entregarlo a un objeto COM. La duración de `pSchemaRowset` está enlazada por `ppRowset`.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Esta función implementa un creador genérico para todos los tipos de conjuntos de filas de esquema. Normalmente, el usuario no llama a esta función. Se llama mediante la implementación de la asignación de esquema.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (clase)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)