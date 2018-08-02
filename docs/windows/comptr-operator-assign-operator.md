---
title: 'Comptr:: operator = (operador) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fac3a845ea7c512f5a7ccffdabdf67ce26029ff8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466168"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= (Operador)
Asigna un valor a la actual **ComPtr**.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *U*  
 Una clase.  
  
 *other*  
 Un puntero, referencia o referencia de valor r a un tipo u otro **ComPtr**.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia a la actual **ComPtr**.  
  
## <a name="remarks"></a>Comentarios  
 La primera versión de este operador asigna un valor vacío a la actual **ComPtr**.  
  
 En la segunda versión, si el puntero de interfaz de asignación no es el mismo que el actual **ComPtr** puntero de interfaz, el segundo puntero de interfaz se asigna a la actual **ComPtr**.  
  
 En la tercera versión, el puntero de interfaz de asignación se asigna a la actual **ComPtr**.  
  
 En la cuarta versión, si el puntero de interfaz de la asignación de valor no es el mismo que el actual **ComPtr** puntero de interfaz, el segundo puntero de interfaz se asigna a la actual **ComPtr**.  
  
 La quinta versión es un operador de copia. una referencia a un **ComPtr** se asigna a la actual **ComPtr**.  
  
 La sexta versión es un operador de copia que usa la semántica; de transferencia una referencia rvalue para un **ComPtr** si es estático cualquier tipo de conversión y, a continuación, se asigna a la actual **ComPtr**.  
  
 La séptima versión es un operador de copia que usa la semántica; de transferencia una referencia rvalue para un **ComPtr** typu *U* es estático, a continuación, convertir y asignado al actual **ComPtr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)