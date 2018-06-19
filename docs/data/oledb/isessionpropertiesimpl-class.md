---
title: ISessionPropertiesImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ISessionPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 62b1321c9d7d50ff2cd459b395efa1e8147a06ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106055"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl (Clase)
Proporciona una implementación de la [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Una clase de propiedad definibles por el usuario que tiene como valor predeterminado `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Devuelve la lista de propiedades en el grupo de propiedades de sesión que están establecidas actualmente en la sesión.|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Establece las propiedades en el grupo de propiedades de la sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en las sesiones. Esta clase implementa las propiedades de la sesión mediante una llamada a una función estática definida por el [mapa de conjunto de propiedades](../../data/oledb/begin-propset-map.md). La asignación de conjunto de propiedad debe especificarse en la clase de sesión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)