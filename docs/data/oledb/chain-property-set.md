---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHAIN_PROPERTY_SET
dev_langs:
- C++
helpviewer_keywords:
- CHAIN_PROPERTY_SET macro
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 634ab21ef9ffa18e5c18efa9078eb0606f9ff387
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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