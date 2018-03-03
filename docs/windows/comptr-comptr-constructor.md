---
title: Constructor de Comptr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8f6234bf2dff0dab801c982a585dc30e338bb7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr (Constructor)
Inicializa una nueva instancia de la clase ComPtr. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 Tipo del parámetro `other`.  
  
 `other`  
 Objeto de tipo `U`.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor es el constructor predeterminado, que implícitamente crea un objeto vacío. El segundo constructor especifica [__nullptr](../windows/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.  
  
 El tercer constructor crea un objeto desde el objeto especificado por un puntero.  
  
 Los constructores cuarto y quinto son constructores de copias. El quinto constructor copia un objeto si es convertible al tipo actual.  
  
 Los constructores sexto y séptimo son constructores de movimiento. El séptimo constructor mueve un objeto si es convertible al tipo actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)