---
title: IRowsetInfoImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
dev_langs: C++
helpviewer_keywords: IRowsetInfoImpl class
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d34fdaa37901d8bdce3dce312d674024a84ad0e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl (Clase)
Proporciona una implementación para el [IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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