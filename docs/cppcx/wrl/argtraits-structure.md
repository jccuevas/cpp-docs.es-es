---
title: ArgTraits (estructura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: 16c44d861ebbbc98fa1bffb62a00d1989c0c803c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377172"
---
# <a name="argtraits-structure"></a>ArgTraits (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

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
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

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
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

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
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>Parámetros

*TMemberFunction*<br/>
Parámetro Typename para una estructura ArgTraits que no puede coincidir con ninguna `Invoke` firma de método.

*TDelegateInterface*<br/>
Una interfaz de delegado.

*TArg1*<br/>
El tipo del primer `Invoke` argumento del método.

*TArg2*<br/>
El tipo del segundo `Invoke` argumento del método.

*TArg3*<br/>
El tipo del tercer `Invoke` argumento del método.

*TArg4*<br/>
El tipo del cuarto `Invoke` argumento del método.

*TArg5*<br/>
El tipo del quinto `Invoke` argumento del método.

*TArg6*<br/>
El tipo del sexto `Invoke` argumento del método.

*TArg7*<br/>
El tipo del séptimo `Invoke` argumento del método.

*TArg8*<br/>
El tipo del octavo `Invoke` argumento del método.

*TArg9*<br/>
El tipo del noveno `Invoke` argumento del método.

## <a name="remarks"></a>Observaciones

La `ArgTraits` estructura declara una interfaz de delegado especificada y una función miembro anónima que tiene un número especificado de parámetros.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre       | Descripción
---------- | ----------------------
`Arg1Type` | El typedef para TArg1.
`Arg2Type` | El typedef para TArg2.
`Arg3Type` | El typedef para TArg3.
`Arg4Type` | El typedef para TArg4.
`Arg5Type` | El typedef para TArg5.
`Arg6Type` | El typedef para TArg6.
`Arg7Type` | El typedef para TArg7.
`Arg8Type` | El typedef para TArg8.
`Arg9Type` | El typedef para TArg9.

### <a name="public-constants"></a>Constantes públicas

Nombre                     | Descripción
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Mantiene el recuento del número `Invoke` de parámetros en el método de una interfaz de delegado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="argtraitsargs"></a><a name="args"></a>ArgTraits::args

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Observaciones

Mantiene el recuento del número `Invoke` de parámetros en el método de una interfaz de delegado. Cuando `args` es igual a -1, no `Invoke` puede haber ninguna coincidencia para la firma del método.
