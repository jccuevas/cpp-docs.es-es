---
title: 'CDynamicAccessor:: Getblobhandling | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- GetBlobHandling method
ms.assetid: bbc6dda6-e132-42a3-980d-24e455cbe456
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec9aa10258a5836a345314ad8820ff320ead1a86
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorgetblobhandling"></a>CDynamicAccessor::GetBlobHandling
Recupera el BLOB de control de valor de la fila actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Devuelve el control de valor de objeto BLOB `eBlobHandling` tal como lo establece [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)