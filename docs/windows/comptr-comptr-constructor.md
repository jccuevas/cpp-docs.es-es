---
title: Constructor de Comptr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86b55d8288f44b04ac1afc30a0afd67fce4edf81
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646778"
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr (Constructor)
Inicializa una nueva instancia de la **ComPtr** clase. Las sobrecargas proporcionan constructores predeterminados, así como de copia, movimiento y conversión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
### <a name="parameters"></a>Parámetros  
 *U*  
 El tipo de la *otros* parámetro.  
  
 *other*  
 Un objeto de tipo *U*.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 El primer constructor es el constructor predeterminado, que implícitamente crea un objeto vacío. Especifica el segundo constructor [__nullptr](../windows/nullptr-cpp-component-extensions.md), que crea explícitamente un objeto vacío.  
  
 El tercer constructor crea un objeto desde el objeto especificado por un puntero.  
  
 Los constructores cuarto y quinto son constructores de copia. El quinto constructor copia un objeto si es convertible al tipo actual.  
  
 Los constructores sexto y séptimo son constructores de movimiento. El séptimo constructor mueve un objeto si es convertible al tipo actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)