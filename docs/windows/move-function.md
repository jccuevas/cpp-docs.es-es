---
title: Move (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
dev_langs:
- C++
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 879bd0a0652e593c968bbc286cf977d7ec8d4e56
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="move-function"></a>Move (función)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class T>  
inline typename RemoveReference<T>::Type&& Move(  
   _Inout_ T&& arg  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo del argumento.  
  
 `arg`  
 Argumento pasado a mover.  
  
## <a name="return-value"></a>Valor devuelto  
 Parámetro `arg` después de rasgos de referencia o referencia rvalue, si los hay, se han quitado.  
  
## <a name="remarks"></a>Comentarios  
 Mueve el argumento especificado de una ubicación a otra.  
  
 Para obtener más información, consulte el **mover semántica** sección de [declarador de referencia Rvalue: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)