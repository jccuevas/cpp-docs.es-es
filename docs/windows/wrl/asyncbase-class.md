---
title: AsyncBase (clase)
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 367d0b0cd3197623b27ee1a50e804cca797aedf3
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337500"
---
# <a name="asyncbase-class"></a>AsyncBase (clase)

Implementa la máquina de estados asincrónica de Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parámetros

*TComplete*<br/>
Un controlador de eventos que se llama cuando finaliza una operación asincrónica.

*TProgress*<br/>
Un controlador de eventos que se llama cuando una operación asincrónica notifica el progreso actual de la operación.

*resultType*<br/>
Uno de los [AsyncResultType](asyncresulttype-enumeration.md) valores de enumeración. De forma predeterminada, `SingleResult`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                               | Descripción
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Inicializa una instancia de la clase `AsyncBase`.

### <a name="public-methods"></a>Métodos públicos

Name                                         | Descripción
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Cancel](#cancel)                 | Cancela una operación asincrónica.
[AsyncBase::Close](#close)                   | Cierra la operación asincrónica.
[AsyncBase::FireCompletion](#firecompletion) | Invoca el controlador de eventos de finalización o restablece al delegado de progreso interno.
[AsyncBase::FireProgress](#fireprogress)     | Invoca el controlador de eventos de progreso actual.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Recupera el código de error para la operación asincrónica actual.
[AsyncBase::get_Id](#get-id)                 | Recupera el identificador de la operación asincrónica.
[AsyncBase::get_Status](#get-status)         | Recupera un valor que indica el estado de la operación asincrónica.
[AsyncBase::GetOnComplete](#getoncomplete)   | Copia la dirección del controlador de eventos de finalización actual a la variable especificada.
[AsyncBase::GetOnProgress](#getonprogress)   | Copia la dirección del controlador de eventos de progreso actual en la variable especificada.
[AsyncBase::put_Id](#put-id)                 | Establece el identificador de la operación asincrónica.
[AsyncBase::PutOnComplete](#putoncomplete)   | Establece la dirección del controlador de eventos de finalización en el valor especificado.
[AsyncBase::PutOnProgress](#putonprogress)   | Establece la dirección del controlador de eventos de progreso en el valor especificado.


### <a name="protected-methods"></a>Métodos protegidos

Name                                                                         | Descripción
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Comprueba si se pueden modificar las propiedades de delegado en el estado asincrónico actual.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Comprueba si se pueden recopilar los resultados de una operación asincrónica en el estado asincrónico actual.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Determina si la operación asincrónica, debe continuar el procesamiento o debería detenerse.
[AsyncBase::CurrentStatus](#currentstatus)                                   | Recupera el estado de la operación asincrónica actual.
[AsyncBase::ErrorCode](#errorcode)                                           | Recupera el código de error para la operación asincrónica actual.
[AsyncBase::OnCancel](#oncancel)                                             | Cuando se invalida en una clase derivada, cancela una operación asincrónica.
[AsyncBase::OnClose](#onclose)                                               | Cuando se invalida en una clase derivada, cierra una operación asincrónica.
[AsyncBase::OnStart](#onstart)                                               | Cuando se invalida en una clase derivada, comienza una operación asincrónica.
[AsyncBase::Start](#start)                                                   | Inicia la operación asincrónica.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Indica si se ha completado la operación asincrónica actual.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Indica si el código de error especificado puede modificar el estado de error interno.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres**: Microsoft::WRL

## <a name="asyncbase"></a>AsyncBase::AsyncBase

Inicializa una instancia de la clase `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="cancel"></a>AsyncBase::Cancel

Cancela una operación asincrónica.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, siempre devuelve S_OK.

### <a name="remarks"></a>Comentarios

`Cancel()` es una implementación predeterminada de `IAsyncInfo::Cancel`, y no se realiza ningún trabajo real. Para cancelar realmente una operación asincrónica, invalidar el `OnCancel()` método virtual puro.

## <a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Comprueba si se pueden modificar las propiedades de delegado en el estado asincrónico actual.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se pueden modificar las propiedades de delegado; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Comprueba si se pueden recopilar los resultados de una operación asincrónica en el estado asincrónico actual.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se pueden recopilar los resultados; en caso contrario, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="close"></a>AsyncBase::Close

Cierra la operación asincrónica.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Valor devuelto

S_OK si la operación cierra o ya está cerrado; en caso contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Comentarios

`Close()` es una implementación predeterminada de `IAsyncInfo::Close`, y no se realiza ningún trabajo real. Para cerrar realmente una operación asincrónica, invalidar el `OnClose()` método virtual puro.

## <a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Determina si la operación asincrónica, debe continuar el procesamiento o debería detenerse.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Valor devuelto

**True** si el estado actual de la operación asincrónica es *iniciado*, lo que significa que la operación debe continuar. En caso contrario, **false**, lo que significa que la operación debe detenerse.

## <a name="currentstatus"></a>AsyncBase::CurrentStatus

Recupera el estado de la operación asincrónica actual.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parámetros

*status*<br/>
La ubicación donde esta operación almacena el estado actual.

### <a name="remarks"></a>Comentarios

Esta operación es segura para subprocesos.

## <a name="errorcode"></a>AsyncBase::ErrorCode

Recupera el código de error para la operación asincrónica actual.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
La ubicación donde esta operación almacena el código de error actual.

### <a name="remarks"></a>Comentarios

Esta operación es segura para subprocesos.

## <a name="firecompletion"></a>AsyncBase::FireCompletion

Invoca el controlador de eventos de finalización o restablece al delegado de progreso interno.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Comentarios

La primera versión de `FireCompletion()` restablece la variable de delegado de progreso interno. La segunda versión invoca el controlador de eventos de finalización si se ha completado la operación asincrónica.

## <a name="fireprogress"></a>AsyncBase::FireProgress

Invoca el controlador de eventos de progreso actual.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parámetros

*arg*<br/>
Método de controlador de eventos que se va a invocar.

### <a name="remarks"></a>Comentarios

`ProgressTraits` se deriva de [ArgTraitsHelper (estructura)](argtraitshelper-structure.md).

## <a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Recupera el código de error para la operación asincrónica actual.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parámetros

*errorCode*<br/>
La ubicación donde se almacena el código de error actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL si la operación asincrónica actual está cerrada.

## <a name="get-id"></a>AsyncBase::get_Id

Recupera el identificador de la operación asincrónica.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
La ubicación donde se almacenará el identificador.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Comentarios

Este método implementa `IAsyncInfo::get_Id`.

## <a name="get-status"></a>AsyncBase::get_Status

Recupera un valor que indica el estado de la operación asincrónica.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parámetros

*status*<br/>
La ubicación donde se almacenará el estado. Para obtener más información, consulte `Windows::Foundation::AsyncStatus` enumeración.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Comentarios

Este método implementa `IAsyncInfo::get_Status`.

## <a name="getoncomplete"></a>AsyncBase::GetOnComplete

Copia la dirección del controlador de eventos de finalización actual a la variable especificada.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*<br/>
La ubicación donde se almacena la dirección del controlador de eventos de finalización actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="getonprogress"></a>AsyncBase::GetOnProgress

Copia la dirección del controlador de eventos de progreso actual en la variable especificada.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parámetros

*progressHandler*<br/>
La ubicación donde se almacena la dirección del controlador de eventos de progreso actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="oncancel"></a>AsyncBase::OnCancel

Cuando se invalida en una clase derivada, cancela una operación asincrónica.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="onclose"></a>AsyncBase::OnClose

Cuando se invalida en una clase derivada, cierra una operación asincrónica.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="onstart"></a>AsyncBase::OnStart

Cuando se invalida en una clase derivada, comienza una operación asincrónica.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="put-id"></a>AsyncBase::put_Id

Establece el identificador de la operación asincrónica.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parámetros

*identificador*<br/>
Un identificador distinto de cero.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_INVALIDARG o E_ILLEGAL_METHOD_CALL.

## <a name="putoncomplete"></a>AsyncBase::PutOnComplete

Establece la dirección del controlador de eventos de finalización en el valor especificado.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*<br/>
La dirección a la que se establece el controlador de eventos de finalización.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="putonprogress"></a>AsyncBase::PutOnProgress

Establece la dirección del controlador de eventos de progreso en el valor especificado.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parámetros

*progressHandler*<br/>
La dirección a la que se establece el controlador de eventos de progreso.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="start"></a>AsyncBase::Start

Inicia la operación asincrónica.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Valor devuelto

S_OK si la operación se inicia o ya está iniciado; en caso contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Comentarios

`Start()` es un método protegido que no es visible externamente, dado que las operaciones asincrónicas "" hot"inicio" antes de devolver al llamador.

## <a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Indica si se ha completado la operación asincrónica actual.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Valor devuelto

**True** si se ha completado la operación asincrónica; en caso contrario, **false**.

## <a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Indica si el código de error especificado puede modificar el estado de error interno.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
Un HRESULT de error.

### <a name="return-value"></a>Valor devuelto

**True** si el estado de error interno se ha cambiado; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Esta operación modifica el estado de error únicamente si el estado de error ya está establecido en S_OK. Esta operación no tiene ningún efecto si el estado de error ya es error, cancelado, completado o cerrado.
