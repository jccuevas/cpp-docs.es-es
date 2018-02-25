---
title: END_ACCESSOR_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- END_ACCESSOR_MAP
dev_langs:
- C++
helpviewer_keywords:
- END_ACCESSOR_MAP macro
ms.assetid: ede813c7-46c9-48a6-aa1a-8ebf38e92023
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: de0bdf9a4e3827272edaaa8a3eae905946de0cf2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="endaccessormap"></a>END_ACCESSOR_MAP
Marca el final de las entradas del mapa de descriptor de acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
END_ACCESSOR_MAP()  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Para varios descriptores de acceso en un conjunto de filas, debe especificar `BEGIN_ACCESSOR_MAP` y usar el `BEGIN_ACCESSOR` macro para cada descriptor de acceso individual. La macro `BEGIN_ACCESSOR` se completa con la macro `END_ACCESSOR` . El `BEGIN_ACCESSOR_MAP` macro se ha completado con el `END_ACCESSOR_MAP` macro.  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)