---
title: IRowsetUpdateImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c49782328ed51afe6a6501ed239d0800221864c3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl (Clase)
La implementación de plantillas OLE DB de la [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de `IRowsetUpdateImpl`.  
  
 `Storage`  
 El registro de usuario.  
  
 `UpdateArray`  
 Matriz que contiene los datos almacenados en caché para actualizar el conjunto de filas.  
  
 `RowClass`  
 La unidad de almacenamiento para el **HROW**.  
  
 `MapClass`  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)  
  
|||  
|-|-|  
|[SetData](../../data/oledb/irowsetupdateimpl-setdata.md)|Establece los valores de datos en una o varias columnas.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Métodos de interfaz (usados con IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](../../data/oledb/irowsetupdateimpl-getoriginaldata.md)|Obtiene los datos transmitidos a más recientemente u obtenido del origen de datos, pasando por alto los cambios pendientes.|  
|[GetPendingRows](../../data/oledb/irowsetupdateimpl-getpendingrows.md)|Devuelve una lista de filas con cambios pendientes.|  
|[GetRowStatus](../../data/oledb/irowsetupdateimpl-getrowstatus.md)|Devuelve el estado de las filas especificadas.|  
|[Undo](../../data/oledb/irowsetupdateimpl-undo.md)|Deshace los cambios realizados en la fila desde la última captura o de actualización.|  
|[Actualizar](../../data/oledb/irowsetupdateimpl-update.md)|Transmite los cambios realizados en la fila desde la última captura o de actualización.|  
  
### <a name="implementation-methods-callback"></a>Métodos de implementación (devolución de llamada)  
  
|||  
|-|-|  
|[IsUpdateAllowed](../../data/oledb/irowsetupdateimpl-isupdateallowed.md)|Se usa para comprobar la seguridad, la integridad, y así sucesivamente antes de permitir las actualizaciones.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_mapCachedData](../../data/oledb/irowsetupdateimpl-m-mapcacheddata.md)|Contiene los datos originales para la operación diferida.|  
  
## <a name="remarks"></a>Comentarios  
 En primer lugar debe leer y entender la documentación de [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx), porque todo lo descrito se aplica también a continuación. También debe leer el capítulo 6 de la *referencia del programador de OLE DB* acerca de cómo configurar los datos.  
  
 `IRowsetUpdateImpl` implementa OLE DB `IRowsetUpdate` interfaz, que permite a los consumidores retrasar la transmisión de los cambios realizados con `IRowsetChange` al origen de datos y deshacer los cambios antes de la transmisión.  
  
> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la siguiente documentación antes de intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Capítulo 6 de la *referencia del programador OLE DB*  
  
-   Consulte también cómo `RUpdateRowset` clase se utiliza en el ejemplo UpdatePV  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)