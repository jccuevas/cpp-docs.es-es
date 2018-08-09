---
title: Método Handlenulltraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 6fb2fa0d-df20-45dc-856f-f78497f8bdf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0206433d2b329501b10a8262e7b487ec83e99302
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642115"
---
# <a name="handlenulltraitsclose-method"></a>HANDLENullTraits::Close (Método)
Cierra el identificador especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline static bool Close(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Para cerrar el identificador.  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si controlar *h* cerrado correctamente; en caso contrario, **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [HANDLENullTraits (estructura)](../windows/handlenulltraits-structure.md)