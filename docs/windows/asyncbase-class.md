---
title: AsyncBase (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cba5aaaec3303d9cd3534ff86cb677219c9c81c7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586789"
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

template <
   typename TComplete,
   AsyncResultType resultType
>
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parámetros

*TComplete*  
Un controlador de eventos que se llama cuando finaliza una operación asincrónica.

*TProgress*  
Un controlador de eventos que se llama cuando una operación asincrónica notifica el progreso actual de la operación.

*resultType*  
Uno de los [AsyncResultType](../windows/asyncresulttype-enumeration.md) valores de enumeración. De forma predeterminada, `SingleResult`.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[AsyncBase::AsyncBase (constructor)](../windows/asyncbase-asyncbase-constructor.md)|Inicializa una instancia de la **AsyncBase** clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[AsyncBase::Cancel (método)](../windows/asyncbase-cancel-method.md)|Cancela una operación asincrónica.|
|[AsyncBase::Close (método)](../windows/asyncbase-close-method.md)|Cierra la operación asincrónica.|
|[AsyncBase::FireCompletion (método)](../windows/asyncbase-firecompletion-method.md)|Invoca el controlador de eventos de finalización o restablece al delegado de progreso interno.|
|[AsyncBase::FireProgress (método)](../windows/asyncbase-fireprogress-method.md)|Invoca el controlador de eventos de progreso actual.|
|[AsyncBase::get_ErrorCode (método)](../windows/asyncbase-get-errorcode-method.md)|Recupera el código de error para la operación asincrónica actual.|
|[AsyncBase::get_Id (método)](../windows/asyncbase-get-id-method.md)|Recupera el identificador de la operación asincrónica.|
|[AsyncBase::get_Status (método)](../windows/asyncbase-get-status-method.md)|Recupera un valor que indica el estado de la operación asincrónica.|
|[AsyncBase::GetOnComplete (método)](../windows/asyncbase-getoncomplete-method.md)|Copia la dirección del controlador de eventos de finalización actual a la variable especificada.|
|[AsyncBase::GetOnProgress (método)](../windows/asyncbase-getonprogress-method.md)|Copia la dirección del controlador de eventos de progreso actual en la variable especificada.|
|[AsyncBase::put_Id (método)](../windows/asyncbase-put-id-method.md)|Establece el identificador de la operación asincrónica.|
|[AsyncBase::PutOnComplete (método)](../windows/asyncbase-putoncomplete-method.md)|Establece la dirección del controlador de eventos de finalización en el valor especificado.|
|[AsyncBase::PutOnProgress (método)](../windows/asyncbase-putonprogress-method.md)|Establece la dirección del controlador de eventos de progreso en el valor especificado.|
|[AsyncBase::Start (método)](../windows/asyncbase-start-method.md)|Inicia la operación asincrónica.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[AsyncBase::CheckValidStateForDelegateCall (método)](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|Comprueba si se pueden modificar las propiedades de delegado en el estado asincrónico actual.|
|[AsyncBase::CheckValidStateForResultsCall (método)](../windows/asyncbase-checkvalidstateforresultscall-method.md)|Comprueba si se pueden recopilar los resultados de una operación asincrónica en el estado asincrónico actual.|
|[AsyncBase::ContinueAsyncOperation (método)](../windows/asyncbase-continueasyncoperation-method.md)|Determina si la operación asincrónica, debe continuar el procesamiento o debería detenerse.|
|[AsyncBase::CurrentStatus (método)](../windows/asyncbase-currentstatus-method.md)|Recupera el estado de la operación asincrónica actual.|
|[AsyncBase::ErrorCode (método)](../windows/asyncbase-errorcode-method.md)|Recupera el código de error para la operación asincrónica actual.|
|[AsyncBase::OnCancel (método)](../windows/asyncbase-oncancel-method.md)|Cuando se invalida en una clase derivada, cancela una operación asincrónica.|
|[AsyncBase::OnClose (método)](../windows/asyncbase-onclose-method.md)|Cuando se invalida en una clase derivada, cierra una operación asincrónica.|
|[AsyncBase::OnStart (método)](../windows/asyncbase-onstart-method.md)|Cuando se invalida en una clase derivada, comienza una operación asincrónica.|
|[AsyncBase::TryTransitionToCompleted (método)](../windows/asyncbase-trytransitiontocompleted-method.md)|Indica si se ha completado la operación asincrónica actual.|
|[AsyncBase::TryTransitionToError (método)](../windows/asyncbase-trytransitiontoerror-method.md)|Indica si el código de error especificado puede modificar el estado de error interno.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)