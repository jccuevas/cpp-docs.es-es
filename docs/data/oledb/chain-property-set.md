---
title: CHAIN_PROPERTY_SET | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.openlocfilehash: f5a80f6c834c3359d3a4be40b892ff4e5600e9e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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