---
title: IRowsetLocateImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetLocateImpl
dev_langs:
- C++
helpviewer_keywords:
- providers, bookmarks
- IRowsetLocateImpl class
- bookmarks, OLE DB
ms.assetid: a8aa3149-7ce8-4976-a680-2da193fd3234
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e2a43df3d8732734ed79aae4c56a891bd20bbebe
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetlocateimpl-class"></a>IRowsetLocateImpl (Clase)
Implementa OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfaz, que captura filas arbitrarias desde un conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class RowsetInterface,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap < RowClass::KeyType, RowClass* >,   
   class BookmarkKeyType = LONG,   
   class BookmarkType = LONG,   
   class BookmarkMapClass = CAtlMap < RowClass::KeyType, RowClass* >>  
class ATL_NO_VTABLE IRowsetLocateImpl : public IRowsetImpl<  
       T,   
       RowsetInterface,   
       RowClass,   
       MapClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de `IRowsetLocateImpl`.  
  
 `RowsetInterface`  
 Una clase derivada de `IRowsetImpl`.  
  
 `RowClass`  
 La unidad de almacenamiento para el **HROW**.  
  
 `MapClass`  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  
  
 `BookmarkKeyType`  
 El tipo del marcador, como un valor largo o una cadena. Marcadores normales deben tener una longitud de al menos dos bytes. (Longitud de un solo byte está reservado para OLE DB [marcadores estándares](https://msdn.microsoft.com/en-us/library/ms712954.aspx)**DBBMK_FIRST**, **DBBMK_LAST**, y **DBBMK_INVALID**.)  
  
 `BookmarkType`  
 El mecanismo de asignación para mantener las relaciones de marcador para los datos.  
  
 `BookmarkMapClass`  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el marcador.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[Compare](../../data/oledb/irowsetlocateimpl-compare.md)|Compara dos marcadores.|  
|[GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)|Captura filas a partir de la fila especificada por un desplazamiento de un marcador.|  
|[GetRowsByBookmark](../../data/oledb/irowsetlocateimpl-getrowsbybookmark.md)|Captura las filas que coinciden con los marcadores especificados.|  
|[Hash](../../data/oledb/irowsetlocateimpl-hash.md)|Devuelve el hash valores para los marcadores especificados.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_rgBookmarks](../../data/oledb/irowsetlocateimpl-m-rgbookmarks.md)|Una matriz de marcadores.|  
  
## <a name="remarks"></a>Comentarios  
 `IRowsetLocateImpl` es la implementación de plantillas OLE DB de la [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfaz. `IRowsetLocate` se utiliza para capturar filas arbitrarias de un conjunto de filas. Un conjunto de filas que implementan esta interfaz es un `sequential` conjunto de filas. Cuando `IRowsetLocate` está presente en un conjunto de filas, la columna 0 es el marcador de las filas; leer esta columna, se obtendrá un valor de marcador que puede usarse para cambiar la posición en la misma fila.  
  
 `IRowsetLocateImpl` se utiliza para implementar la compatibilidad con marcadores en proveedores. Los marcadores son marcadores de posición (índices en un conjunto de filas) que permiten al consumidor volver rápidamente a una fila, lo que permite acceso a los datos de alta velocidad. El proveedor determina qué marcadores forma única pueden identificar una fila. Usar `IRowsetLocateImpl` métodos, puede comparar los marcadores, fetch filas por offset, fetch filas por marcador y devuelven valores de hash de marcadores.  
  
 Para admitir marcadores de OLE DB en un conjunto de filas, haga que el conjunto de filas herede de esta clase.  
  
 Para obtener información sobre cómo implementar la compatibilidad con marcadores, vea [proveedor admite marcadores](../../data/oledb/provider-support-for-bookmarks.md) en el *Guía del programador de Visual C++* y [marcadores](https://msdn.microsoft.com/en-us/library/ms709728.aspx) en el *Referencia del programador OLE DB* en Platform SDK.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [IRowsetLocate:IRowset](https://msdn.microsoft.com/en-us/library/ms721190.aspx)   
 [Compatibilidad del proveedor con los marcadores](../../data/oledb/provider-support-for-bookmarks.md)   
 [Marcadores](https://msdn.microsoft.com/en-us/library/ms709728.aspx)