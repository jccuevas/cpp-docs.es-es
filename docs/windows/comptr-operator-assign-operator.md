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
ms.openlocfilehash: 177d6ebde6a4611e9a08dc3dade63bd6c3acc3fa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401633"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= (Operador)

Asigna un valor a la actual **ComPtr**.

## <a name="syntax"></a>Sintaxis

```cpp
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

### <a name="parameters"></a>Parámetros

*U*<br/>
Una clase.

*other*<br/>
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