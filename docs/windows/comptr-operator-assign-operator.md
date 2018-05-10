---
title: 'Comptr:: operator = (operador) | Documentos de Microsoft'
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
ms.openlocfilehash: f4066db37de8a993802970784f09141352fef028
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="comptroperator-operator"></a>ComPtr::operator= (Operador)
Asigna un valor a la ComPtr actual.  
  
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
 `U`  
 Una clase.  
  
 `other`  
 Una referencia de puntero, referencia o valor r a un tipo u otro ComPtr.  
  
## <a name="return-value"></a>Valor devuelto  
 Una referencia a la ComPtr actual.  
  
## <a name="remarks"></a>Comentarios  
 La primera versión de este operador asigna un valor vacío a la ComPtr actual.  
  
 En la segunda versión, si el puntero de interfaz de asignación no es el mismo que el puntero de interfaz de ComPtr actual, se asigna el segundo puntero de interfaz a la ComPtr actual.  
  
 En la tercera versión, el puntero de interfaz asignar se asigna a la ComPtr actual.  
  
 En la cuarta versión, si el puntero de interfaz del valor de asignación no es el mismo que el puntero de interfaz de ComPtr actual, se asigna el segundo puntero de interfaz a la ComPtr actual.  
  
 La versión del quinto es un operador de copia. una referencia a una ComPtr se asigna a la ComPtr actual.  
  
 La versión del sexto es mover de un operador de copia que usa la semántica; una referencia a valor r en una ComPtr si es estático cualquier tipo de conversión y, a continuación, se asigna a la ComPtr actual.  
  
 La versión del séptima es mover de un operador de copia que usa la semántica; una referencia a valor r a una ComPtr de tipo `U` es estático, a continuación, convierte y asignada a la ComPtr actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)