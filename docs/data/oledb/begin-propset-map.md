---
title: BEGIN_PROPSET_MAP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- BEGIN_PROPSET_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPSET_MAP macro
ms.assetid: c3a30618-6025-4d49-8688-a171294d2e93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5b1596797672c0fff92531ff90f67b94bfd6101e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="beginpropsetmap"></a>BEGIN_PROPSET_MAP
Las marcas de principio de la propiedad establece entradas del mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Clase*  
 [in] La clase en la que se especifica esta propiedad establecida. Un conjunto de propiedades puede especificarse en los siguientes objetos de OLE DB:  
  
-   [Objetos de origen de datos](https://msdn.microsoft.com/en-us/library/ms721278.aspx)  
  
-   [Objetos de sesión](https://msdn.microsoft.com/en-us/library/ms711572.aspx)  
  
-   [Comandos](https://msdn.microsoft.com/en-us/library/ms724608.aspx)  
  
## <a name="example"></a>Ejemplo  
 Esta es una asignación de conjunto de propiedades de ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)