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
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821719"
---
# <a name="argtraits-structure"></a>ArgTraits (estructura)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

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

### <a name="parameters"></a>Parameters

*TMemberFunction*<br/>
Parámetro TypeName para una estructura Argtraits (que no puede coincidir con ninguna firma de método `Invoke`.

*TDelegateInterface*<br/>
Interfaz de delegado.

*TArg1*<br/>
Tipo del primer argumento del método `Invoke`.

*TArg2*<br/>
Tipo del segundo argumento del método `Invoke`.

*TArg3*<br/>
Tipo del tercer argumento del método `Invoke`.

*TArg4*<br/>
Tipo del cuarto argumento del método de `Invoke`.

*TArg5*<br/>
Tipo del quinto argumento del método de `Invoke`.

*TArg6*<br/>
Tipo del sexto argumento del método `Invoke`.

*TArg7*<br/>
Tipo del séptimo argumento del método `Invoke`.

*TArg8*<br/>
Tipo del octavo argumento del método `Invoke`.

*TArg9*<br/>
Tipo del noveno argumento del método `Invoke`.

## <a name="remarks"></a>Notas

La estructura `ArgTraits` declara una interfaz de delegado especificada y una función miembro anónima que tiene un número especificado de parámetros.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Typedefs públicos

Name       | Descripción
---------- | ----------------------
`Arg1Type` | La definición de tipo para TArg1.
`Arg2Type` | La definición de tipo para TArg2.
`Arg3Type` | La definición de tipo para TArg3.
`Arg4Type` | La definición de tipo para TArg4.
`Arg5Type` | La definición de tipo para TArg5.
`Arg6Type` | La definición de tipo para TArg6.
`Arg7Type` | La definición de tipo para TArg7.
`Arg8Type` | La definición de tipo para TArg8.
`Arg9Type` | La definición de tipo para TArg9.

### <a name="public-constants"></a>Constantes públicas

Name                     | Descripción
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits::args](#args) | Mantiene el recuento del número de parámetros en el método de `Invoke` de una interfaz de delegado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ArgTraits`

## <a name="requirements"></a>Requisitos de

**Encabezado:** Event. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="args"></a>ArgTraits::args

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Notas

Mantiene el recuento del número de parámetros en el método de `Invoke` de una interfaz de delegado. Cuando `args` es igual a-1, no puede haber ninguna coincidencia para la firma del método `Invoke`.
