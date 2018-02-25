---
title: IColumnsInfoImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e775e0836d27cf055990a2e9bc3bf2f07e61225e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl (Clase)
Proporciona una implementación de la [IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IColumnsInfoImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/icolumnsinfoimpl-getcolumninfo.md)|Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.|  
|[MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)|Devuelve una matriz de ordinales de las columnas de un conjunto de filas que se identifican mediante los identificadores de columna especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en conjuntos de filas y comandos. Para modificar el comportamiento de su proveedor `IColumnsInfo` implementación, debe modificar la asignación de columna de proveedor.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)