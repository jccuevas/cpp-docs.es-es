---
title: CHAIN_PROPERTY_SET | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9db57535f3f0bc7653c80b83c3e0115727eed707
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094340"
---
# <a name="chainpropertyset"></a>CHAIN_PROPERTY_SET
Esta macro encadena grupos de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ChainClass*  
 [in] El nombre de la clase a las propiedades de cadena para. Se trata de una clase generada por el Asistente para proyectos de ATL que ya contiene un mapa (por ejemplo, una clase de objeto origen de datos, comando o sesión).  
  
## <a name="remarks"></a>Comentarios  
 Puede encadenar un conjunto de propiedades de otra clase en su propia clase, a continuación, obtener acceso a las propiedades directamente desde la clase.  
  
> [!CAUTION]
>  Use esta macro con moderación. El uso incorrecto puede hacer que un consumidor a producirá un error en las pruebas de conformidad de OLE DB.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)