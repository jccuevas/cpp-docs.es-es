---
title: Método Handlet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: f7df0f90-fafb-4d1b-a215-a6c62941f6b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7bf4a6fab735708295a0ae229e7b47101ecc115b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648397"
---
# <a name="handletdetach-method"></a>HandleT::Detach (Método)
Desasocia actual **HandleT** objeto a partir de su identificador subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typename HandleTraits::Type Detach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El identificador subyacente.  
  
## <a name="remarks"></a>Comentarios  
 Cuando finalice esta operación, actual **HandleT** está establecido en el estado no válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [HandleT (clase)](../windows/handlet-class.md)