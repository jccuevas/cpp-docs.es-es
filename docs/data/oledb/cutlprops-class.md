---
title: CUtlProps (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CUtlProps
dev_langs: C++
helpviewer_keywords: CUtlProps class
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 75e92f48729d0aae9f85cc7b7c5c97e4778f96a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cutlprops-class"></a>CUtlProps (Clase)
Implementa las propiedades para una variedad de interfaces de la propiedad de OLE DB (por ejemplo, `IDBProperties`, `IDBProperties`, y `IRowsetInfo`).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase que contiene el `BEGIN_PROPSET_MAP`.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|Obtiene una propiedad de un conjunto de propiedades.|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|Se utiliza para validar un valor antes de establecer una propiedad.|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|Administra las solicitudes de una interfaz opcional cuando un consumidor llama a un método de la interfaz de creación de un objeto.|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|Se llama después de establecer una propiedad que se va a administrar propiedades encadenadas.|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|Establece una propiedad en un conjunto de propiedades.|  
  
## <a name="remarks"></a>Comentarios  
 La mayor parte de esta clase es un detalle de implementación.  
  
 `CUtlProps`contiene dos miembros para establecer las propiedades internamente: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) y [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Para obtener más información sobre las macros utilizadas en una asignación de conjunto de propiedades, vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) y [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)