---
title: IRowsetImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetImpl class
ms.assetid: 6a9189af-7556-45b1-adcb-9d62bb36704c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0ca6d35eeea1dbfae4f2a5bb1b2ee93553e53519
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimpl-class"></a>IRowsetImpl (Clase)
Proporciona una implementación de la `IRowset` interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class RowsetInterface,  
   class RowClass = CSimpleRow,  
   class MapClass = CAtlMap <  
      RowClass::KeyType,  
      RowClass*>>  
class ATL_NO_VTABLE IRowsetImpl : public RowsetInterface  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IRowsetImpl`.  
  
 `RowsetInterface`  
 Una clase derivada de `IRowsetImpl`.  
  
 `RowClass`  
 Unidad de almacenamiento para el **HROW**.  
  
 `MapClass`  
 Unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md)|Agrega un recuento de referencias a un identificador de fila existente.|  
|[CreateRow](../../data/oledb/irowsetimpl-createrow.md)|Llamado por el método [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) para asignar un nuevo **HROW**. No llama directamente al usuario.|  
|[GetData](../../data/oledb/irowsetimpl-getdata.md)|Recupera datos de la copia del conjunto de filas de la fila.|  
|[GetDBStatus](../../data/oledb/irowsetimpl-getdbstatus.md)|Devuelve el estado para el campo especificado.|  
|[GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md)|Captura filas secuencialmente, teniendo en cuenta la posición anterior.|  
|[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)|El constructor. No llama directamente al usuario.|  
|[RefRows](../../data/oledb/irowsetimpl-refrows.md)|Llamado por el método [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md). No llama directamente al usuario.|  
|[ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)|Versiones de filas.|  
|[RestartPosition](../../data/oledb/irowsetimpl-restartposition.md)|Cambia de posición de la siguiente posición de captura en su posición inicial; es decir, su posición cuando el conjunto de filas fue el primero creado.|  
|[SetDBStatus](../../data/oledb/irowsetimpl-setdbstatus.md)|Establece las marcas de estado para el campo especificado.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)|Indica si un proveedor admite la captura con versiones anteriores.|  
|[m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)|Indica si un proveedor puede tener su desplazamiento de cursor con las versiones anteriores.|  
|[m_bReset](../../data/oledb/irowsetimpl-m-breset.md)|Indica si un proveedor restablece la posición del cursor. Esto tiene un significado especial cuando desplazarse hacia atrás o hacia atrás en la obtención [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md).|  
|[m_iRowset](../../data/oledb/irowsetimpl-m-irowset.md)|Un índice en el conjunto de filas, que representa el cursor.|  
|[m_rgRowHandles](../../data/oledb/irowsetimpl-m-rgrowhandles.md)|Una lista de identificadores de fila.|  
  
## <a name="remarks"></a>Comentarios  
 [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) es la interfaz de conjunto de filas base.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)