---
title: 'CDynamicAccessor:: Getblobhandling | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
dev_langs: C++
helpviewer_keywords: GetBlobHandling method
ms.assetid: bbc6dda6-e132-42a3-980d-24e455cbe456
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b9bac84019f408c7a68cf6afbffe94572be44c46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetblobhandling"></a>CDynamicAccessor::GetBlobHandling
Recupera el BLOB de control de valor de la fila actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
const DBBLOBHANDLINGENUM GetBlobHandling( ) const;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Devuelve el control de valor de objeto BLOB `eBlobHandling` tal como lo establece [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)