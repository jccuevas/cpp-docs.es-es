---
title: 'CDynamicAccessor:: Getblobsizelimit | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
dev_langs: C++
helpviewer_keywords: GetBlobSizeLimit method
ms.assetid: 7131e7c4-6e05-42f3-9d87-110301b672f2
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3162ee335902b887facbc6e3aec33523622be5f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicaccessorgetblobsizelimit"></a>CDynamicAccessor::GetBlobSizeLimit
Recupera el tamaño máximo de BLOB en bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
const DBLENGTH GetBlobSizeLimit( ) const;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Devuelve el control de valor de objeto BLOB `nBlobSize` tal como lo establece [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)