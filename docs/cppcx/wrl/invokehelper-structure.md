---
title: InvokeHelper (estructura)
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371382"
---
# <a name="invokehelper-structure"></a>InvokeHelper (estructura)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>Parámetros

*TDelegateInterface*<br/>
El tipo de interfaz de delegado.

*TCallback*<br/>
El tipo de la función de controlador de eventos.

*argCount*<br/>
El número de argumentos en una especialización. `InvokeHelper`

## <a name="remarks"></a>Observaciones

Proporciona una implementación del `Invoke()` método en función del número especificado y el tipo de argumentos.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre     | Descripción
-------- | -----------------------------------------------------------------------------
`Traits` | Sinónimo de la clase que define el tipo de cada argumento de controlador de eventos.

### <a name="public-constructors"></a>Constructores públicos

Nombre                                        | Descripción
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Inicializa una nueva instancia de la clase `InvokeHelper`.

### <a name="public-methods"></a>Métodos públicos

Nombre                            | Descripción
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.

### <a name="public-data-members"></a>Miembros de datos públicos

Nombre                                 | Descripción
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Representa el controlador de eventos que se va a llamar cuando se produce un evento.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InvokeHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL::Details

## <a name="invokehelpercallback_"></a><a name="callback"></a>InvokeHelper::callback_

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Observaciones

Representa el controlador de eventos que se va a llamar cuando se produce un evento.

El `TCallback` parámetro template especifica el tipo del controlador de eventos.

## <a name="invokehelperinvoke"></a><a name="invoke"></a>InvokeHelper::Invoke

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
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

*arg1*<br/>
Argumento 1.

*arg2*<br/>
Argumento 2.

*arg3*<br/>
Argumento 3.

*arg4*<br/>
Argumento 4.

*arg5*<br/>
Argumento 5.

*arg6*<br/>
Argumento 6.

*arg7*<br/>
Argumento 7.

*arg8*<br/>
Argumento 8.

*arg9*<br/>
Argumento 9.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que describe el error.

### <a name="remarks"></a>Observaciones

Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>InvokeHelper::InvokeHelper

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parámetros

*devolución de llamada*<br/>
Un controlador de eventos.

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `InvokeHelper`.

El `TCallback` parámetro template especifica el tipo del controlador de eventos.
