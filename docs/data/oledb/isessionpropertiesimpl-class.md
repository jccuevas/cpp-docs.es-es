---
title: ISessionPropertiesImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ISessionPropertiesImpl
dev_langs: C++
helpviewer_keywords: ISessionPropertiesImpl class
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ff8eda4d593ff0c6064313a7be243ec498b15c4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl (Clase)
Proporciona una implementación de la [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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