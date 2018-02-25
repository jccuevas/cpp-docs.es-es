---
title: IRowsetCreatorImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IRowsetCreatorImpl
- ATL.IRowsetCreatorImpl
- ATL::IRowsetCreatorImpl<T>
- ATL.IRowsetCreatorImpl<T>
- IRowsetCreatorImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetCreatorImpl class
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51d984f2254c8a2a135b5ecb386e8f195946366b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetcreatorimpl-class"></a>IRowsetCreatorImpl (Clase)
Realiza las mismas funciones que `IObjectWithSite` , pero también permite que las propiedades de OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de **IRowsetCreator**.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|Establece el sitio que contiene el objeto de conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase hereda de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) e invalida [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). Cuando un objeto de comando o una sesión de proveedor crea un conjunto de filas, llama al método `QueryInterface` en el objeto de conjunto de filas buscando `IObjectWithSite` y llamadas `SetSite` pasar el objeto de conjunto de filas **IUnkown** interfaz como la interfaz de sitio.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)