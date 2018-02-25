---
title: IDBSchemaRowsetImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBSchemaRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBSchemaRowsetImpl class
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2895aeebd49e38b157ab55912fcc4b7c52ba953e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl (clase)
Proporciona la implementación de conjuntos de filas de esquema.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class SessionClass>  
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset  
```  
  
#### <a name="parameters"></a>Parámetros  
 `SessionClass`  
 La clase por la que `IDBSchemaRowsetImpl` se hereda. Normalmente, esta clase será la clase de sesión del usuario.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)|Comprueba la validez de las restricciones en un conjunto de filas de esquema.|  
|[CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)|Implementa una función de creación de objetos COM para el objeto especificado por el parámetro de la plantilla.|  
|[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)|Especifica qué restricciones se admiten en un conjunto de filas de esquema determinado.|  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)|Devuelve un conjunto de filas de esquema.|  
|[GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)|Devuelve una lista de conjuntos de filas de esquema accesibles por [IDBSchemaRowsetImpl::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md).|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase implementa la interfaz [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) y la función de creador de plantillas [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md).  
  
 OLE DB usa conjuntos de filas de esquema para devolver datos sobre los datos de un proveedor. Estos datos se suelen denominar "metadatos". De forma predeterminada, un proveedor siempre debe admitir `DBSCHEMA_TABLES`, **DBSCHEMA_COLUMNS**y **DBSCHEMA_PROVIDER_TYPES**, como se describe en [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en la *Referencia del programador de OLE DB*. Conjuntos de filas de esquema se designan en una asignación de esquema. Para obtener información sobre las entradas de asignación de esquema, vea [SCHEMA_ENTRY](../../data/oledb/schema-entry.md).  
  
 El Asistente para proveedores OLE DB, en el Asistente para objetos ATL, genera automáticamente el código para los conjuntos de filas de esquema en el proyecto. (De forma predeterminada, el asistente admite conjuntos de filas de esquema obligatorios mencionados anteriormente). Cuando crea un consumidor mediante el Asistente para objetos ATL, el asistente usa conjuntos de filas de esquema para enlazar los datos correctos a un proveedor. Si no implementa los conjuntos de filas de esquema para proporcionar los metadatos correctos, el asistente no enlazará los datos correctos.  
  
 Para obtener más información sobre la compatibilidad del proveedor con los conjuntos de filas de esquema, vea [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).  
  
 Para obtener más información sobre los conjuntos de filas de esquema, vea [Conjuntos de filas de esquema](https://msdn.microsoft.com/en-us/library/ms712921.aspx) en la *Referencia del programador de OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Miembros de IDBSchemaRowsetImpl (clase)](http://msdn.microsoft.com/en-us/e74f6f82-541c-42e7-b4c6-e2d4656a0649)   
 [Clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)   
 [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md)