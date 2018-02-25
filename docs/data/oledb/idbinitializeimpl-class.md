---
title: IDBInitializeImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
dev_langs:
- C++
helpviewer_keywords:
- IDBInitializeImpl class
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 60fba7a37147a4ab5bb6847a945bf9ffec3706da
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl (Clase)
Proporciona una implementación para el [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IDBInitializeImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|El constructor.|  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[Initialize](../../data/oledb/idbinitializeimpl-initialize.md)|Inicia el proveedor.|  
|[Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)|Detiene el proveedor.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|Marcas del origen de datos.|  
|[m_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|Un puntero a la implementación de la información de propiedades de la base de datos.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en los objetos de origen de datos y la interfaz opcional sobre los enumeradores.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)