---
title: Clase AgileEventSource
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: fa1e0a72d865b2993e149f6e4d2b57fe13463a61
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821745"
---
# <a name="agileeventsource-class"></a>Clase AgileEventSource

Representa un evento generado por un componente ágil, que es un componente al que se puede tener acceso desde cualquier subproceso. Hereda de [EventSource](eventsource-class.md) e invalida la función miembro `Add` con un parámetro de tipo adicional para especificar las opciones para invocar el evento Agile.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parameters

*TDelegateInterface*<br/>
La interfaz a un delegado que representa un controlador de eventos.

*TEventSourceOptions*<br/>
Estructura [InvokeModeOptions](invokemodeoptions-structure.md) cuyo campo invokeMode se establece en `InvokeMode::StopOnFirstError` o `InvokeMode::FireAll`.

## <a name="remarks"></a>Notas

La gran mayoría de los componentes del Windows Runtime son componentes ágiles. Para obtener más información, vea [subprocesamiento y serializaciónC++(/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Requisitos de

**Encabezado:** Event. h

**Espacio de nombres:** Microsoft::WRL

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[AgileEventSource:: Add (método)](#add)|Anexa el controlador de eventos ágil que representa la interfaz de delegado especificada al conjunto de controladores de eventos para el objeto **AgileEventSource** actual.|

## <a name="add"></a>AgileEventSource:: Add (método)

Anexa el controlador de eventos representado por la interfaz de delegado especificada al conjunto de controladores de eventos para el objeto [EventSource](eventsource-class.md) actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parameters

*delegateInterface*<br/>
La interfaz de un objeto delegado, que representa un controlador de eventos.

*token*<br/>
Cuando se completa esta operación, un identificador que representa el evento. Use este token como parámetro para el método `Remove()` para descartar el controlador de eventos.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)