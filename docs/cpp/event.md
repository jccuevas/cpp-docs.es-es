---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: f8935408c6e9b43347d4ad6088505a461e254ae2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366302"
---
# <a name="__event"></a>__event

Declara un evento.

## <a name="syntax"></a>Sintaxis

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>Observaciones

La palabra clave **__event** se puede aplicar a una declaración de método, una declaración de interfaz o una declaración de miembro de datos. Sin embargo, no puede usar la palabra clave **__event** para calificar a un miembro de una clase anidada.

Dependiendo de si el origen y el receptor del evento son C++ nativo, COM o administrados (.NET Framework), puede usar las siguientes construcciones como eventos:

|C++ nativo|COM|Administrada (.NET Framework)|
|------------------|---------|--------------------------------|
|Método|—|método|
|—|interfaz|—|
|—|—|miembro de datos|

Utilice [__hook](../cpp/hook.md) en un receptor de eventos para asociar un método de controlador con un método de evento. Tenga en cuenta que después de crear un evento con la palabra clave **__event,** se llamará a todos los controladores de eventos conectados posteriormente a ese evento cuando se llame al evento.

Una declaración de método **__event** no puede tener una definición; una definición se genera implícitamente, por lo que se puede llamar al método de evento como si fuera cualquier método ordinario.

> [!NOTE]
> Una clase o struct basada en plantilla no puede contener eventos.

## <a name="native-events"></a>Eventos nativos

Los eventos nativos son métodos. El tipo de valor devuelto suele ser HRESULT o **void**, pero puede ser cualquier tipo entero, incluida una **enumeración.** Cuando un evento usa un tipo de valor devuelto entero, se define una condición de error cuando un controlador de eventos devuelve un valor distinto de cero, en cuyo caso el evento que se provoca llama a los otros delegados.

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

Consulte Control de eventos [en C+ nativo](../cpp/event-handling-in-native-cpp.md) para obtener código de ejemplo.

## <a name="com-events"></a>Eventos COM

Los eventos COM son interfaces. Los parámetros de un método en una interfaz de origen de eventos deben estar *en* parámetros (pero esto no se aplica rigurosamente), porque un parámetro *out* no es útil al multidifusión. Se emitirá una advertencia de nivel 1 si utiliza un parámetro *out.*

El tipo de valor devuelto suele ser HRESULT o **void**, pero puede ser cualquier tipo entero, incluida **enum**. Cuando un evento usa un tipo de valor devuelto entero y un controlador de eventos devuelve un valor distinto de cero se produce un estado de error, en cuyo caso el evento que se provoca anula las llamadas a los otros delegados. Tenga en cuenta que el compilador marcará automáticamente una interfaz de origen de eventos como [origen](../windows/attributes/source-cpp.md) en el IDL generado.

La palabra clave [__interface](../cpp/interface.md) siempre es necesaria después de **__event** para un origen de eventos COM.

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

Consulte Control de eventos [en COM](../cpp/event-handling-in-com.md) para obtener código de ejemplo.

## <a name="managed-events"></a>Eventos administrados

Para obtener información sobre la codificación de eventos en la nueva sintaxis, consulte [evento](../extensions/event-cpp-component-extensions.md).

Los eventos administrados son miembros de datos o métodos. Cuando se utiliza con un evento, el tipo de valor devuelto de un delegado debe ser compatible con [Common Language Specification](/dotnet/standard/language-independence-and-language-independent-components). El tipo de valor devuelto del controlador de eventos debe coincidir con el del delegado. Para obtener más información sobre los delegados, vea [Delegados y eventos](../dotnet/delegates-and-events.md). Si un evento administrado es un miembro de datos, el tipo debe ser un puntero a un delegado.

En .NET Framework, puede tratar un miembro de datos como si se tratara de un método en sí mismo (es decir, el método `Invoke` de su delegado correspondiente). Debe predefinir el tipo de delegado para declarar un miembro de datos de evento administrado. En cambio, un método de evento administrado define implícitamente el delegado administrado correspondiente si todavía no se ha definido. Por ejemplo, puede declarar un valor de evento tal como `OnClick` como evento de la manera siguiente:

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

Al declarar implícitamente un evento administrado, puede especificar que se agreguen y quiten los descriptores de acceso a los que se llamará cuando se agreguen o quiten los controladores de eventos. También puede definir el método que llama (genera) el evento desde fuera de la clase.

## <a name="example-native-events"></a>Ejemplo: eventos nativos

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>Ejemplo: eventos COM

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Manejo de eventos](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
