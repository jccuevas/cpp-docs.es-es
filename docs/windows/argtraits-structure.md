---
title: ArgTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
dev_langs:
- C++
helpviewer_keywords:
- ArgTraits structure
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 047754338566d476fa8e832d58dd2d4cd0776a63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418403"
---
# <a name="argtraits-structure"></a>ArgTraits (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TMemberFunction>
struct ArgTraits;
template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;
template<
   typename TDelegateInterface,
   typename TArg1
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;
template<
   typename TDelegateInterface,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parámetros

*TMemberFunction*<br/>
Parámetro TypeName para una ArgTraits (estructura) que no coincide con ninguna `Invoke` firma del método.

*TDelegateInterface*<br/>
Una interfaz de delegado.

*TArg1*<br/>
El tipo del primer argumento de la `Invoke` método.

*TArg2*<br/>
El tipo del segundo argumento de la `Invoke` método.

*TArg3*<br/>
El tipo del tercer argumento de la `Invoke` método.

*TArg4*<br/>
El tipo del cuarto argumento de la `Invoke` método.

*TArg5*<br/>
El tipo del quinto argumento de la `Invoke` método.

*TArg6*<br/>
El tipo del sexto argumento de la `Invoke` método.

*TArg7*<br/>
El tipo del séptimo argumento de la `Invoke` método.

*TArg8*<br/>
El tipo del octavo argumento de la `Invoke` método.

*TArg9*<br/>
El tipo del noveno argumento de la `Invoke` método.

## <a name="remarks"></a>Comentarios

El **ArgTraits** estructura declara un delegado especificado de interfaz y una función miembro anónimo que tiene un número especificado de parámetros.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`Arg1Type`|La definición de tipo para TArg1.|
|`Arg2Type`|La definición de tipo para TArg2.|
|`Arg3Type`|La definición de tipo para TArg3.|
|`Arg4Type`|La definición de tipo para TArg4.|
|`Arg5Type`|La definición de tipo para TArg5.|
|`Arg6Type`|La definición de tipo para TArg6.|
|`Arg7Type`|La definición de tipo para TArg7.|
|`Arg8Type`|La definición de tipo para TArg8.|
|`Arg9Type`|La definición de tipo para TArg9.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[ArgTraits::args (constante)](../windows/argtraits-args-constant.md)|Mantiene un recuento del número de parámetros el `Invoke` al método de interfaz de un delegado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)