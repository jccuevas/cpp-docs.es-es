---
title: BEGIN_ACCESSOR | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_ACCESSOR
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
ms.assetid: 59d0ff3e-7cfd-4ce8-9a1c-d664c0892a52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39307534a9622160d6620b8d1c501cb112dbc717
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="beginaccessor"></a>BEGIN_ACCESSOR
Marca el principio de una entrada de descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BEGIN_ACCESSOR(num, bAuto)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *num*  
 [in] El número de desplazamiento cero para el descriptor de acceso en este mapa de descriptor de acceso.  
  
 *bAuto*  
 [in] Especifica si este descriptor de acceso es un descriptor de acceso automático o un descriptor de acceso manual. Si **true**, el descriptor de acceso es automático; si **false**, el descriptor de acceso es manual. Un descriptor de acceso automático significa datos se capturan automáticamente en las operaciones de movimiento.  
  
## <a name="remarks"></a>Comentarios  
 En el caso de varios descriptores de acceso en un conjunto de filas, debe especificar `BEGIN_ACCESSOR_MAP` y usar el `BEGIN_ACCESSOR` macro para cada descriptor de acceso individual. La macro `BEGIN_ACCESSOR` se completa con la macro `END_ACCESSOR` . El `BEGIN_ACCESSOR_MAP` macro se ha completado con el `END_ACCESSOR_MAP` macro.  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)