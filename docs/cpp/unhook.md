---
title: __unhook
ms.date: 11/04/2016
f1_keywords:
- __unhook
- __unhook_cpp
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
ms.openlocfilehash: 221ffc30a9b8a40c44f8009dfa511b72aa160e01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337563"
---
# <a name="__unhook"></a>__unhook

Disocia un método de control de un evento.

## <a name="syntax"></a>Sintaxis

```cpp
long  __unhook(
   &SourceClass::EventMethod,
   source,
   &ReceiverClass::HandlerMethod
   [, receiver = this]
);
long  __unhook(
   interface,
   source
);
long  __unhook(
   source
);
```

#### <a name="parameters"></a>Parámetros

**&***SourceClass* `::` *EventMethod* Un puntero al método de evento desde el que se desengancha el método de controlador de eventos:

- Eventos nativos de C++: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

- Eventos COM: *SourceClass* es la interfaz de origen de eventos y *EventMethod* es uno de sus métodos.

- Eventos administrados: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

*interfaz*<br/>
El nombre de interfaz que se desengancha del *receptor,* solo para los receptores de eventos COM en los que el parámetro *layout_dependent* del atributo [event_receiver](../windows/attributes/event-receiver.md) es **true**.

*de origen*<br/>
Un puntero a una instancia del origen de eventos. Dependiendo del `type` código especificado `event_receiver`en , *source* puede ser uno de los siguientes:

- Un puntero nativo de objeto de origen de eventos.

- Un `IUnknown`puntero basado en (origen COM).

- Un puntero de objeto administrado (para eventos administrados).

**&***ReceiverClass* `::` `HandlerMethod` Un puntero al método de controlador de eventos que se va a desenganchar de un evento. El controlador se especifica como un método de una clase o una referencia a la misma; si no especifica el nombre de clase, **__unhook** asume que la clase es aquel en la que se llama.

- Eventos Nativos C++: *ReceiverClass* es `HandlerMethod` la clase de receptor de eventos y es el controlador.

- Eventos COM: *ReceiverClass* es la `HandlerMethod` interfaz del receptor de eventos y es uno de sus controladores.

- Eventos administrados: *ReceiverClass* es `HandlerMethod` la clase de receptor de eventos y es el controlador.

*receptor*(opcional) Un puntero a una instancia de la clase de receptor de eventos. Si no especifica un receptor, el valor predeterminado es la clase o estructura receptora en la que se llama **a __unhook.**

## <a name="usage"></a>Uso

Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.

## <a name="remarks"></a>Observaciones

Utilice la función intrínseca **__unhook** en un receptor de eventos para disociar o "desenganchar" un método de controlador de un método de evento.

Hay tres formas de **__unhook.** Puede usar la primera forma (cuatro argumento) en la mayoría de los casos. Puede utilizar la segunda forma (dos argumentos) de **__unhook** solo para un receptor de eventos COM; esto desengancha toda la interfaz de eventos. Puede utilizar la tercera forma (un argumento) para desenlazar todos los delegados del origen especificado.

Un valor devuelto distinto de cero indica que se ha producido un error (los eventos administrados producirán una excepción).

Si llama a **__unhook** en un controlador de eventos y eventos que aún no están conectados, no tendrá ningún efecto.

En tiempo de compilación, el compilador comprueba que el evento existe y realiza la comprobación de tipo de parámetros con el controlador especificado.

Con la excepción de los eventos COM, se puede llamar **a __hook** y **__unhook** fuera del receptor de eventos.

Una alternativa al uso de **__unhook** es utilizar el operador - .

Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, consulte [evento](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="example"></a>Ejemplo

Consulte Control de eventos [en C+ nativo](../cpp/event-handling-in-native-cpp.md) y Control de eventos [en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
