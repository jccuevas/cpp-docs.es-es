---
title: IRowsetInfoImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f9b784dbb13ff39be21ccd353d514dd244d5ae41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl (Clase)
Proporciona una implementación para el [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IRowsetInfoImpl`.  
  
 `PropClass`  
 Una clase de propiedad definibles por el usuario que tiene como valor predeterminado `T`.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/irowsetinfoimpl-getproperties.md)|Devuelve la configuración actual de todas las propiedades admitidas por el conjunto de filas.|  
|[GetReferencedRowset](../../data/oledb/irowsetinfoimpl-getreferencedrowset.md)|Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.|  
|[GetSpecification](../../data/oledb/irowsetinfoimpl-getspecification.md)|Devuelve un puntero de interfaz en el objeto (comando o sesión) que creó este conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en conjuntos de filas. Esta clase implementa las propiedades del conjunto de filas mediante la [mapa de conjunto de propiedades](../../data/oledb/begin-propset-map.md) definido en la clase de comando. Aunque parezca que usarán la propiedad de la clase de comando establece la clase de conjunto de filas, el conjunto de filas se suministra con su propia copia de las propiedades de tiempo de ejecución, cuando se crea un objeto de comando o una sesión.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** altdb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)