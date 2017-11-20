---
title: 'IDBSchemaRowsetImpl:: CheckRestrictions | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
dev_langs: C++
helpviewer_keywords: CheckRestrictions method
ms.assetid: 3c9d77d2-0e4b-48fa-80db-d735da19f1cf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d6e057c56e824327d726e073a02f0fa636553c40
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="idbschemarowsetimplcheckrestrictions"></a>IDBSchemaRowsetImpl::CheckRestrictions
Comprueba la validez de las restricciones en un conjunto de filas de esquema.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT CheckRestrictions(  
   REFGUID rguidSchema,  
   ULONG cRestrictions,  
   const VARIANT rgRestrictions[]  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rguidSchema`  
 [in] Referencia al GUID del conjunto de filas de esquema solicitado (por ejemplo, `DBSCHEMA_TABLES`).  
  
 `cRestrictions`  
 [in] Número de restricciones que el consumidor pasó para el conjunto de filas de esquema.  
  
 `rgRestrictions`  
 [in] Matriz de longitud *cRestrictions* de los valores de restricción que se van a establecer. Para obtener más información, vea la descripción del parámetro `rgRestrictions` en [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md).  
  
## <a name="remarks"></a>Comentarios  
 Use `CheckRestrictions` para comprobar la validez de las restricciones en un conjunto de filas de esquema. Comprueba las restricciones para los conjuntos de filas de esquema `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**y **DBSCHEMA_PROVIDER_TYPES** . Llámelo para determinar si la llamada de un consumidor a **IDBSchemaRowset::GetRowset** es correcta. Si quiere admitir conjuntos de filas de esquema distintos de los mencionados anteriormente, debe crear su propia función para llevar a cabo esta tarea.  
  
 `CheckRestrictions` determina si el consumidor llama a [GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) con la restricción correcta y el tipo de restricción correcto (por ejemplo, `VT_BSTR` para una cadena) que admite el proveedor. También determina si se admite el número correcto de restricciones. De forma predeterminada, `CheckRestrictions` le preguntará al proveedor mediante la llamada [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) cuáles son las restricciones que admite en un conjunto de filas determinado. Después, compara las restricciones del consumidor con las que admite el proveedor y la operación se realiza correctamente o bien se produce un error.  
  
 Para obtener más información sobre conjuntos de filas de esquema, consulte [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el *referencia del programador de OLE DB* del SDK de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (clase)](../../data/oledb/idbschemarowsetimpl-class.md)   
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)