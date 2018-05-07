---
title: ICommandPropertiesImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25be1548bd41f832a007f102c138fc01f8818774
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl (Clase)
Proporciona una implementación de la [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase, derivada de  
  
 `PropClass`  
 La clase de propiedades.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Devuelve la lista de propiedades en el grupo de propiedades de conjunto de filas que actualmente se solicitan para el conjunto de filas.|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Establece las propiedades en el grupo de propiedades de conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Esto es obligatorio en comandos. Proporciona la implementación de una función estática definida por el [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) macro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)