---
title: IRowsetChangeImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b289e20f4714503e0aef6deb2273f6cd12192e7d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl (Clase)
La implementación de plantillas OLE DB de la [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interfaz en la especificación de OLE DB.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de `IRowsetChangeImpl`.  
  
 `Storage`  
 El registro de usuario.  
  
 `BaseInterface`  
 La clase base para la interfaz, como `IRowsetChange`.  
  
 `RowClass`  
 La unidad de almacenamiento para el identificador de fila.  
  
 `MapClass`  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](../../data/oledb/irowsetchangeimpl-deleterows.md)|Elimina las filas del conjunto de filas.|  
|[InsertRow](../../data/oledb/irowsetchangeimpl-insertrow.md)|Inserta una fila en el conjunto de filas.|  
|[SetData](../../data/oledb/irowsetchangeimpl-setdata.md)|Establece los valores de datos en una o varias columnas.|  
  
### <a name="implementation-method-callback"></a>Método de implementación (devolución de llamada)  
  
|||  
|-|-|  
|[FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md)|Se reemplaza por proveedor para confirmar datos en su almacén.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es responsable de operaciones de escritura inmediato en un almacén de datos. Almacena "Inmediata" significa que, cuando el usuario final (es decir, la persona con el consumidor) realiza los cambios, esos cambios se transfieren inmediatamente a los datos (y no se puede deshacer).  
  
 `IRowsetChangeImpl` implementa OLE DB `IRowsetChange` interfaz, lo que permite la actualización de los valores de columnas en las filas existentes, eliminar filas e insertar nuevas filas.  
  
 La implementación de plantillas OLE DB admite todos los métodos base (`SetData`, `InsertRow`, y `DeleteRows`).  
  
> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la siguiente documentación antes de intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Capítulo 6 de la *referencia del programador OLE DB*  
  
-   Consulte también cómo `RUpdateRowset` clase se utiliza en el ejemplo UpdatePV  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)