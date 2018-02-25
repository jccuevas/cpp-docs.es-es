---
title: PROPERTY_INFO_ENTRY_VALUE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROPERTY_INFO_ENTRY_VALUE
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY_VALUE macro
ms.assetid: 9690f7f3-fb20-4a7e-a75f-8a3a1cb1ce0d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8adb8fb0c2978bdf5886d47fa0ee33cba8f8fbe4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="propertyinfoentryvalue"></a>PROPERTY_INFO_ENTRY_VALUE
Representa una propiedad concreta de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID  
, value )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropID*  
 [in] Valor [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.  
  
 *valor*  
 [in] El valor de la propiedad de tipo `DWORD`.  
  
## <a name="remarks"></a>Comentarios  
 Con esta macro, puede especificar directamente el valor de propiedad de tipo `DWORD`. Para establecer la propiedad en el valor predeterminado definido en ATLDB. H, use [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Para establecer el valor, marcas y las opciones para la propiedad, utilice [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)