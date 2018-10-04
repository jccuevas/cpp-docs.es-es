---
title: InvokeHelper (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 46cd067e41fcc9ac0d8d3dd9fe50c9edd23532c3
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789116"
---
# <a name="invokehelper-structure"></a>InvokeHelper (estructura)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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
*TCallback*  
El tipo de la función de controlador de eventos.

*argCount*<br/>
El número de argumentos en una `InvokeHelper` especialización.

## <a name="remarks"></a>Comentarios

Proporciona una implementación de la `Invoke()` método según el número especificado y el tipo de argumentos.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name     | Descripción
-------- | -----------------------------------------------------------------------------
`Traits` | Un sinónimo de la clase que define el tipo de cada argumento de controlador de eventos.

### <a name="public-constructors"></a>Constructores públicos

Name                                        | Descripción
------------------------------------------- | -------------------------------------------------------
[Invokehelper](#invokehelper) | Inicializa una nueva instancia de la clase `InvokeHelper`.

### <a name="public-methods"></a>Métodos públicos

Name                            | Descripción
------------------------------- | -----------------------------------------------------------------------------------
[Invokehelper](#invoke) | Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.

### <a name="public-data-members"></a>Miembros de datos públicos

Name                                 | Descripción
------------------------------------ | ----------------------------------------------------------
[Callback_](#callback) | Representa el controlador de eventos al que llamar cuando se produce un evento.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`InvokeHelper`

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Namespace:** wrl

## <a name="callback"></a>Callback_

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Comentarios

Representa el controlador de eventos al que llamar cuando se produce un evento.

El `TCallback` parámetro de plantilla especifica el tipo del controlador de eventos.

## <a name="invoke"></a>Invokehelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

*Arg1*<br/>
Argumento 1.

*Arg2*<br/>
Argumento 2.

*Arg3*<br/>
Argumento 3.

*Arg4*<br/>
Argumento de 4.

*Arg5*<br/>
Argumento de 5.

*Arg6*<br/>
Argumento 6.

*Arg7*<br/>
Argumento de 7.

*Arg8*<br/>
Argumento de 8.

*Arg9*<br/>
Argumento de 9.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que describe el error.

### <a name="remarks"></a>Comentarios

Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.

## <a name="invokehelper"></a>Invokehelper

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parámetros

*devolución de llamada*<br/>
Un controlador de eventos.

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `InvokeHelper`.

El `TCallback` parámetro de plantilla especifica el tipo del controlador de eventos.
