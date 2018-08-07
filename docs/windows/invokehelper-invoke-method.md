---
title: Método Invokehelper | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
dev_langs:
- C++
helpviewer_keywords:
- Invoke method
ms.assetid: 98618815-c30e-4699-b3dd-203c91b1bf3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8db9d9b44a2646d69dfbbd423d712f0d1c92d6cd
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607977"
---
# <a name="invokehelperinvoke-method"></a>InvokeHelper::Invoke (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   Invoke  
)();  
STDMETHOD(  
   Invoke  
)(typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
STDMETHOD(  
   Invoke  
)( typename Traits;  
```  
  
### <a name="parameters"></a>Parámetros  
 *Arg1*  
 Argumento 1.  
  
 *Arg2*  
 Argumento 2.  
  
 *Arg3*  
 Argumento 3.  
  
 *Arg4*  
 Argumento de 4.  
  
 *Arg5*  
 Argumento de 5.  
  
 *Arg6*  
 Argumento 6.  
  
 *Arg7*  
 Argumento de 7.  
  
 *Arg8*  
 Argumento de 8.  
  
 *Arg9*  
 Argumento de 9.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.  
  
## <a name="remarks"></a>Comentarios  
 Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [InvokeHelper (estructura)](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)