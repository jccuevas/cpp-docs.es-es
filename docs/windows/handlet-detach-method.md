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
ms.openlocfilehash: cc11d6be992584adb1ce2075e73d080cc3a43f47
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569484"
---
# <a name="handletdetach-method"></a>HandleT::Detach (Método)
Desasocia actual **HandleT** objeto a partir de su identificador subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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