---
title: __hook
ms.date: 11/04/2016
f1_keywords:
- __hook_cpp
helpviewer_keywords:
- __hook keyword [C++]
- event handlers [C++], connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
ms.openlocfilehash: c4887d85e01344c171fb0fdfe957f2d8a669ff6a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771674"
---
# <a name="hook"></a>__hook

Asocia un método de control a un evento.

## <a name="syntax"></a>Sintaxis

```
long __hook(
    &SourceClass::EventMethod,
    source,
    &ReceiverClass::HandlerMethod
    [, receiver = this]
);
long __hook(
    interface,
    source
);
```

### <a name="parameters"></a>Parámetros

*&SourceClass::EventMethod*<br/>
Un puntero al método de evento al que se enlaza el método de controlador de eventos:

- Eventos de C++ nativo: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

- Eventos COM: *SourceClass* es la interfaz de origen de eventos y *EventMethod* es uno de sus métodos.

- Eventos administrados: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

*interface*<br/>
El nombre de la interfaz que se va a enlazar a *receptor*, solo para los receptores de eventos COM en el que el *layout_dependent* parámetro de la [event_receiver](../windows/attributes/event-receiver.md) atributo es **true**.

*source*<br/>
Un puntero a una instancia del origen de eventos. Según el código de `type` especificado en `event_receiver`, *origen* puede ser uno de los siguientes:

- Un puntero nativo de objeto de origen de eventos.

- Un `IUnknown`-en función de puntero (origen COM).

- Un puntero de objeto administrado (para eventos administrados).

*&ReceiverClass::HandlerMethod*<br/>
Un puntero al método de controlador de eventos que se a enlazar a un evento. El controlador se especifica como un método de una clase o una referencia a la misma; Si no especifica el nombre de clase, **__hook** se da por supuesto que en el que se llama la clase.

- Eventos de C++ nativo: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.

- Eventos COM: *ReceiverClass* es la interfaz de receptor de eventos y `HandlerMethod` es uno de sus controladores.

- Eventos administrados: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.

*receiver*<br/>
(Opcional) Un puntero a una instancia de la clase del receptor de eventos. Si no especifica un receptor, el valor predeterminado es la clase del receptor o estructura en la que **__hook** se llama.

## <a name="usage"></a>Uso

Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.

## <a name="remarks"></a>Comentarios

Utilice la función intrínseca **__hook** en un receptor de eventos para asociar o enlazar un método de controlador con un método de evento. Después se llama al controlador especificado cuando el origen provoca el evento especificado. Puede enlazar varios controladores a un único evento o enlazar varios eventos a un único controlador.

Hay dos formas de **__hook**. Puede usar la primera forma (cuatro argumento) en la mayoría de los casos, en concreto, para los receptores de eventos COM en el que el *layout_dependent* parámetro de la [event_receiver](../windows/attributes/event-receiver.md) atributo es **false** .

En estos casos no necesita enlazar todos los métodos en una interfaz antes de desencadenar un evento en uno de los métodos; solo debe enlazarse el método que controlará el evento. Puede usar la segunda forma (dos argumentos) de **__hook** solo para un receptor de eventos COM en el que *layout_dependent* **= true**.

**__hook** devuelve un valor largo. Un valor devuelto distinto de cero indica que se ha producido un error (los eventos administrados producirán una excepción).

El compilador comprueba la existencia de un evento y que la firma del evento coincida con la firma del delegado.

A excepción de los eventos COM, **__hook** y **__unhook** puede llamarse fuera del receptor de eventos.

Una alternativa al uso **__hook** consiste en usar el operador +=.

Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, vea [eventos](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="example"></a>Ejemplo

Consulte [control de eventos en C++ nativo](../cpp/event-handling-in-native-cpp.md) y [control de eventos en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Control de eventos](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)<br/>
