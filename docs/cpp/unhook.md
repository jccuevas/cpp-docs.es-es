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
ms.openlocfilehash: 2a259b80b941e37e0c3040ad55894c114fe4bc82
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160533"
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

**&** *SourceClass* `::` *EventMethod* un puntero al método de evento desde el que se desenlaza el método de controlador de eventos:

- Eventos C++ nativos: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

- Eventos COM: *SourceClass* es la interfaz de origen de eventos y *EventMethod* es uno de sus métodos.

- Eventos administrados: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.

*interface*<br/>
Nombre de la interfaz que se va a desenlazar del *receptor*, solo para los receptores de eventos com en los que el parámetro *layout_dependent* del atributo [event_receiver](../windows/attributes/event-receiver.md) sea **true**.

*de origen*<br/>
Un puntero a una instancia del origen de eventos. Dependiendo del `type` de código especificado en `event_receiver`, *source* puede ser uno de los siguientes:

- Un puntero nativo de objeto de origen de eventos.

- Puntero basado en `IUnknown`(origen COM).

- Un puntero de objeto administrado (para eventos administrados).

**&** *ReceiverClass* `::` `HandlerMethod` un puntero al método de controlador de eventos que se va a Desenlazar de un evento. El controlador se especifica como un método de una clase o una referencia al mismo; Si no especifica el nombre de clase, **__unhook** supone que la clase es la que se llama.

- Eventos C++ nativos: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.

- Eventos COM: *ReceiverClass* es la interfaz del receptor de eventos y `HandlerMethod` es uno de sus controladores.

- Eventos administrados: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.

*Receiver*(opcional) un puntero a una instancia de la clase de receptor de eventos. Si no especifica un receptor, el valor predeterminado es la clase o estructura del receptor en la que se llama a **__unhook** .

## <a name="usage"></a>Uso

Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.

## <a name="remarks"></a>Observaciones

Use la función intrínseca **__unhook** en un receptor de eventos para desasociar o "Desenlazar" un método de controlador de un método de evento.

Hay tres formas de **__unhook**. Puede usar la primera forma (cuatro argumento) en la mayoría de los casos. Puede usar el segundo formulario (dos argumentos) de **__unhook** solo para un receptor de eventos com; Esto desenlaza la interfaz de eventos completa. Puede utilizar la tercera forma (un argumento) para desenlazar todos los delegados del origen especificado.

Un valor devuelto distinto de cero indica que se ha producido un error (los eventos administrados producirán una excepción).

Si llama a **__unhook** en un evento y un controlador de eventos que todavía no están enlazados, no tendrá ningún efecto.

En tiempo de compilación, el compilador comprueba que el evento existe y realiza la comprobación de tipo de parámetros con el controlador especificado.

A excepción de los eventos COM, se puede llamar a **__hook** y **__unhook** fuera del receptor de eventos.

Una alternativa al uso de **__unhook** es usar el operador-=.

Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, vea [Event](../extensions/event-cpp-component-extensions.md).

> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.

## <a name="example"></a>Ejemplo

Vea [control de eventos en C++ ](../cpp/event-handling-in-native-cpp.md) el control de eventos y nativo [en com](../cpp/event-handling-in-com.md) para obtener ejemplos.

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__event](../cpp/event.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__raise](../cpp/raise.md)
