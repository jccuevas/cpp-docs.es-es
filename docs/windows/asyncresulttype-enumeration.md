---
title: AsyncResultType (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8171c4a57621a4f17a5f0ddb0745faa70fde6524
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465290"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (enumeración)
Especifica el tipo de resultado devuelto por la `GetResults()` método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`MultipleResults`|Un conjunto de resultados múltiples, que se presentan progresivamente entre `Start` estado y antes de `Close()` se llama.|  
|`SingleResult`|Un único resultado, que se presenta después de que se produce el evento Complete.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)