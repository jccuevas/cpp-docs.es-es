---
title: "RaiseException (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 380e3792c5b2b9504bec841965e70bd47ec619d4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="raiseexception-function"></a>RaiseException (función)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hr`  
 El código de excepción de la excepción que se está generando; es decir, el valor HRESULT de una operación con errores.  
  
 `dwExceptionFlags`  
 Una marca que indica una excepción continuable (el valor de la marca es cero), o una excepción noncontinuable (el valor de la marca es distinto de cero). De forma predeterminada, la excepción es discontinuo.  
  
## <a name="remarks"></a>Comentarios  
 Produce una excepción en el subproceso que realiza la llamada.  
  
 Para obtener más información, consulte las ventanas **RaiseException** función.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** internal.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)