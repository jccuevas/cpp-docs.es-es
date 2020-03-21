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
ms.openlocfilehash: 09819c9e8dd924581ce8cd67233d273f7e8d62ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079897"
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
Un controlador de eventos al que se llama cuando se completa una operación asincrónica.

*TProgress*<br/>
Un controlador de eventos al que se llama cuando una operación asincrónica en ejecución informa del progreso actual de la operación.

*resultType*<br/>
Uno de los valores de la enumeración [asyncresulttype (](asyncresulttype-enumeration.md) . De manera predeterminada, es `SingleResult`.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

Nombre                               | Descripción
---------------------------------- | -------------------------------------------------
[AsyncBase:: AsyncBase](#asyncbase) | Inicializa una instancia de la clase `AsyncBase`.

### <a name="public-methods"></a>Métodos públicos

Nombre                                         | Descripción
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase:: CANCEL](#cancel)                 | Cancela una operación asincrónica.
[AsyncBase:: Close](#close)                   | Cierra la operación asincrónica.
[AsyncBase:: Firecompletion (](#firecompletion) | Invoca el controlador de eventos de finalización o restablece el delegado de progreso interno.
[AsyncBase:: Fireprogress (](#fireprogress)     | Invoca el controlador de eventos de progreso actual.
[AsyncBase:: get_ErrorCode](#get-errorcode)   | Recupera el código de error de la operación asincrónica actual.
[AsyncBase:: get_Id](#get-id)                 | Recupera el identificador de la operación asincrónica.
[AsyncBase:: get_Status](#get-status)         | Recupera un valor que indica el estado de la operación asincrónica.
[AsyncBase:: Getoncomplete (](#getoncomplete)   | Copia la dirección del controlador de eventos de finalización actual a la variable especificada.
[AsyncBase:: Getonprogress (](#getonprogress)   | Copia la dirección del controlador de eventos de progreso actual a la variable especificada.
[AsyncBase::p ut_Id](#put-id)                 | Establece el identificador de la operación asincrónica.
[AsyncBase::P utOnComplete](#putoncomplete)   | Establece la dirección del controlador de eventos de finalización en el valor especificado.
[AsyncBase::P utOnProgress](#putonprogress)   | Establece la dirección del controlador de eventos de progreso en el valor especificado.

### <a name="protected-methods"></a>Métodos protegidos

Nombre                                                                         | Descripción
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase:: Checkvalidstatefordelegatecall (](#checkvalidstatefordelegatecall) | Comprueba si las propiedades del delegado se pueden modificar en el estado asincrónico actual.
[AsyncBase:: Checkvalidstateforresultscall (](#checkvalidstateforresultscall)   | Comprueba si los resultados de una operación asincrónica se pueden recopilar en el estado asincrónico actual.
[AsyncBase:: Continueasyncoperation (](#continueasyncoperation)                 | Determina si la operación asincrónica debe continuar el procesamiento o se debe detener.
[AsyncBase:: currentStatus (](#currentstatus)                                   | Recupera el estado de la operación asincrónica actual.
[AsyncBase:: ErrorCode](#errorcode)                                           | Recupera el código de error de la operación asincrónica actual.
[AsyncBase:: OnCancel](#oncancel)                                             | Cuando se reemplaza en una clase derivada, cancela una operación asincrónica.
[AsyncBase:: OnClose](#onclose)                                               | Cuando se reemplaza en una clase derivada, cierra una operación asincrónica.
[AsyncBase:: OnStart](#onstart)                                               | Cuando se reemplaza en una clase derivada, inicia una operación asincrónica.
[AsyncBase:: Start](#start)                                                   | Inicia la operación asincrónica.
[AsyncBase:: Trytransitiontocompleted (](#trytransitiontocompleted)             | Indica si se ha completado la operación asincrónica actual.
[AsyncBase:: Trytransitiontoerror (](#trytransitiontoerror)                     | Indica si el código de error especificado puede modificar el estado de error interno.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** Async. h

**Espacio de nombres:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase:: AsyncBase

Inicializa una instancia de la clase `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase:: CANCEL

Cancela una operación asincrónica.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Valor devuelto

De forma predeterminada, siempre Devuelve S_OK.

### <a name="remarks"></a>Observaciones

`Cancel()` es una implementación predeterminada de `IAsyncInfo::Cancel`y no realiza ningún trabajo real. Para cancelar realmente una operación asincrónica, invalide el método virtual puro `OnCancel()`.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase:: Checkvalidstatefordelegatecall (

Comprueba si las propiedades del delegado se pueden modificar en el estado asincrónico actual.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se pueden modificar las propiedades del delegado; de lo contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase:: Checkvalidstateforresultscall (

Comprueba si los resultados de una operación asincrónica se pueden recopilar en el estado asincrónico actual.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Valor devuelto

S_OK si se pueden recopilar los resultados; de lo contrario, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase:: Close

Cierra la operación asincrónica.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Valor devuelto

S_OK si la operación se cierra o ya está cerrada; de lo contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Observaciones

`Close()` es una implementación predeterminada de `IAsyncInfo::Close`y no realiza ningún trabajo real. Para cerrar realmente una operación asincrónica, invalide el método virtual puro `OnClose()`.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase:: Continueasyncoperation (

Determina si la operación asincrónica debe continuar el procesamiento o se debe detener.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Valor devuelto

**true** si se *inicia*el estado actual de la operación asincrónica, lo que significa que la operación debe continuar. De lo contrario, **false**, lo que significa que la operación se debe detener.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase:: currentStatus (

Recupera el estado de la operación asincrónica actual.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parámetros

*status*<br/>
Ubicación en la que esta operación almacena el estado actual.

### <a name="remarks"></a>Observaciones

Esta operación es segura para subprocesos.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase:: ErrorCode

Recupera el código de error de la operación asincrónica actual.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
Ubicación en la que esta operación almacena el código de error actual.

### <a name="remarks"></a>Observaciones

Esta operación es segura para subprocesos.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase:: Firecompletion (

Invoca el controlador de eventos de finalización o restablece el delegado de progreso interno.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Observaciones

La primera versión de `FireCompletion()` restablece la variable de delegado de progreso interno. La segunda versión invoca el controlador de eventos de finalización si la operación asincrónica ha finalizado.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase:: Fireprogress (

Invoca el controlador de eventos de progreso actual.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parámetros

*arg*<br/>
Método de control de eventos que se va a invocar.

### <a name="remarks"></a>Observaciones

`ProgressTraits` se deriva de la [estructura argtraitshelper (](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase:: get_ErrorCode

Recupera el código de error de la operación asincrónica actual.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parámetros

*errorCode*<br/>
La ubicación donde se almacena el código de error actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL si la operación asincrónica actual está cerrada.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase:: get_Id

Recupera el identificador de la operación asincrónica.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parámetros

*id*<br/>
La ubicación donde se almacenará el identificador.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Observaciones

Este método implementa `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase:: get_Status

Recupera un valor que indica el estado de la operación asincrónica.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parámetros

*status*<br/>
Ubicación en la que se va a almacenar el estado. Para obtener más información, vea enumeración de `Windows::Foundation::AsyncStatus`.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Observaciones

Este método implementa `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase:: Getoncomplete (

Copia la dirección del controlador de eventos de finalización actual a la variable especificada.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*<br/>
Ubicación donde se almacena la dirección del controlador de eventos de finalización actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase:: Getonprogress (

Copia la dirección del controlador de eventos de progreso actual a la variable especificada.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parámetros

*progressHandler*<br/>
Ubicación donde se almacena la dirección del controlador de eventos de progreso actual.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase:: OnCancel

Cuando se reemplaza en una clase derivada, cancela una operación asincrónica.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase:: OnClose

Cuando se reemplaza en una clase derivada, cierra una operación asincrónica.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase:: OnStart

Cuando se reemplaza en una clase derivada, inicia una operación asincrónica.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::p ut_Id

Establece el identificador de la operación asincrónica.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
Un identificador distinto de cero.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_INVALIDARG o E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::P utOnComplete

Establece la dirección del controlador de eventos de finalización en el valor especificado.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parámetros

*completeHandler*<br/>
Dirección en la que se establece el controlador de eventos de finalización.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::P utOnProgress

Establece la dirección del controlador de eventos de progreso en el valor especificado.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parámetros

*progressHandler*<br/>
Dirección en la que se establece el controlador de eventos progress.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase:: Start

Inicia la operación asincrónica.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Valor devuelto

S_OK si la operación se inicia o ya está iniciada; de lo contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Observaciones

`Start()` es un método protegido que no es visible externamente porque las operaciones asincrónicas "Inicio en caliente" antes de volver al llamador.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase:: Trytransitiontocompleted (

Indica si se ha completado la operación asincrónica actual.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Valor devuelto

**true** si se ha completado la operación asincrónica; en caso contrario, **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase:: Trytransitiontoerror (

Indica si el código de error especificado puede modificar el estado de error interno.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parámetros

*error*<br/>
Un valor HRESULT de error.

### <a name="return-value"></a>Valor devuelto

**true** si se cambió el estado de error interno; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Esta operación modifica el estado de error solo si el estado de error ya está establecido en S_OK. Esta operación no tiene ningún efecto si el estado de error ya es error, cancelado, completado o cerrado.
