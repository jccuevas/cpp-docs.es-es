---
title: PROPERTY_INFO_ENTRY | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROPERTY_INFO_ENTRY
dev_langs: C++
helpviewer_keywords: PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8b5193748f7a4f59abb8806e3d09bf0c77274b89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
Representa una propiedad concreta de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
PROPERTY_INFO_ENTRY(  
dwPropID   
)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropID*  
 [in] Valor [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro establece el valor de propiedad de tipo `DWORD` en un valor predeterminado definido en ATLDB. H. Para establecer la propiedad en un valor de su elección, use [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Para establecer el [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) y [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) para la propiedad al mismo tiempo, use [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)