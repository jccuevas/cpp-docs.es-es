---
title: Clase DeferrableEventArgs
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: bae2472a75ab77f138fcee0951a6b869cc7c8e82
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372567"
---
# <a name="deferrableeventargs-class"></a>Clase DeferrableEventArgs

Clase de plantilla usada para los tipos de argumento de evento de los aplazamientos.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parámetros

*TEventArgsInterface*<br/>
El tipo de interfaz que declara los argumentos de un evento diferido.

*TEventArgsClass*<br/>
La clase que implementa *TEventArgsInterface*.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Nombre                                                         | Descripción
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Obtiene una referencia al objeto [Deferral](/uwp/api/windows.foundation.deferral) que representa un evento diferido.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.

## <a name="remarks"></a>Observaciones

Las instancias de esta clase se pasan a los controladores de eventos para eventos diferidos. Los parámetros de plantilla representan una interfaz que define los detalles de los argumentos de evento de un tipo específico de evento diferido y una clase que implementa esa interfaz.

La clase aparece como el primer argumento de un controlador de eventos para un evento diferido. Puede llamar al método [GetDeferral](#getdeferral) para obtener el objeto [Deferral](/uwp/api/windows.foundation.deferral) del que puede obtener toda la información sobre el evento diferido. Tras completar el control de eventos, debe llamar a Complete en el objeto Aplazamiento. A continuación, debe llamar a [InvokeAllFinished](#invokeallfinished) al final del método de controlador de eventos, lo que garantiza que la finalización de todos los eventos diferidos se comunica correctamente.

## <a name="requirements"></a>Requisitos

**Encabezado:** event.h

**Espacio de nombres:** Microsoft::WRL

## <a name="deferrableeventargsgetdeferral"></a><a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Obtiene una referencia al objeto [Deferral](/uwp/api/windows.foundation.deferral) que representa un evento diferido.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parámetros

*Resultado*<br/>
Puntero que hará referencia al objeto [Deferral](/uwp/api/windows.foundation.deferral) cuando se complete la llamada.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.

## <a name="deferrableeventargsinvokeallfinished"></a><a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Observaciones

Debe llamar a este método después de que el origen de eventos llame a [InvokeAll](eventsource-class.md#invokeall). Llamar a este método evita que se realicen futuros aplazamientos y obliga al controlador de finalización a ejecutarse si no se realizaron aplazamientos.
