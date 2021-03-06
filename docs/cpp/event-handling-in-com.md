---
title: Control de eventos en COM
ms.date: 11/04/2016
helpviewer_keywords:
- event handling [C++], COM
- event handling [C++], about event handling
- declaring events
- event handlers [C++], COM
- event handlers
- COM, events
- event receivers, in event handling
- event handling [C++]
- hooking events
- event receivers, name and signature matching
- event sources, in event handling
- declaring events, in COM
- declaring events, event handling in COM
ms.assetid: 6b4617d4-a58e-440c-a8a6-1ad1c715b2bb
ms.openlocfilehash: 756fb6f17aa02fda9a19d501395c39a0b1f602f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366314"
---
# <a name="event-handling-in-com"></a>Control de eventos en COM

En el control de eventos COM, se configura un origen de eventos `type` = `com`y un receptor de eventos mediante los atributos [event_source](../windows/attributes/event-source.md) y [event_receiver,](../windows/attributes/event-receiver.md) respectivamente, especificando . Estos atributos insertan el código adecuado para las interfaces personalizadas, de envío y duales para permitir que las clases a las que se aplican desencadenen eventos y los controlen a través de puntos de conexión de COM.

## <a name="declaring-events"></a>Declarar eventos

En una clase de origen de eventos, utilice la palabra clave [__event](../cpp/event.md) en una declaración de interfaz para declarar los métodos de esa interfaz como eventos. Los eventos de esa interfaz se desencadenan cuando se llaman como métodos de interfaz. Los métodos de las interfaces de eventos pueden tener cero o más parámetros (que deberían estar *todos en* parámetros). El tipo de valor devuelto puede ser void o cualquier tipo entero.

## <a name="defining-event-handlers"></a>Definir controladores de eventos

En una clase de receptor de eventos, se definen los controladores de eventos, que son métodos con firmas (tipos de valor devuelto, convenciones de llamada y argumentos) que coinciden con el evento que van a controlar. Para los eventos COM, las convenciones de llamada no tienen que coincidir; consulte [Eventos COM dependientes del diseño](#vcconeventhandlingincomanchorlayoutdependentcomevents) a continuación para obtener más información.

## <a name="hooking-event-handlers-to-events"></a>Enlazar controladores de eventos a eventos

También en una clase de receptor de eventos, se usa la función intrínseca [__hook](../cpp/hook.md) para asociar eventos con controladores de eventos y [__unhook](../cpp/unhook.md) para disociar eventos de controladores de eventos. Puede enlazar varios eventos a un controlador de eventos o varios controladores de eventos a un evento.

> [!NOTE]
> Normalmente, hay dos técnicas para permitir que un receptor de eventos COM acceda a las definiciones de interfaz del origen de eventos. La primera, mostrada a continuación, es compartir un archivo de encabezado común. El segundo consiste [#import](../preprocessor/hash-import-directive-cpp.md) en `embedded_idl` usar #import con el calificador de importación, de modo que la biblioteca de tipos de origen de eventos se escriba en el archivo .tlh con el código generado por atributos conservado.

## <a name="firing-events"></a>Desencadenar eventos

Para desencadenar un evento, simplemente llame a un método en la interfaz declarada con la palabra clave **__event** en la clase de origen de eventos. Si se han enlazado controladores al evento, se llamará a los controladores.

### <a name="com-event-code"></a>Código de eventos COM

En el ejemplo siguiente se muestra cómo desencadenar un evento en una clase COM. Para compilar y ejecutar el ejemplo, consulte los comentarios del código.

```cpp
// evh_server.h
#pragma once

[ dual, uuid("00000000-0000-0000-0000-000000000001") ]
__interface IEvents {
   [id(1)] HRESULT MyEvent([in] int value);
};

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT FireEvent();
};

class DECLSPEC_UUID("530DF3AD-6936-3214-A83B-27B63C7997C4") CSource;
```

Y después el servidor:

```cpp
// evh_server.cpp
// compile with: /LD
// post-build command: Regsvr32.exe /s evh_server.dll
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include "evh_server.h"

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[coclass, event_source(com), uuid("530DF3AD-6936-3214-A83B-27B63C7997C4")]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      __raise MyEvent(123);
      return S_OK;
   }
};
```

Y después el cliente:

```cpp
// evh_client.cpp
// compile with: /link /OPT:NOREF
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <stdio.h>
#include "evh_server.h"

[ module(name="EventReceiver") ];

[ event_receiver(com) ]
class CReceiver {
public:
   HRESULT MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
      return S_OK;
   }

   HRESULT MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
      return S_OK;
   }

   void HookEvent(IEventSource* pSource) {
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void UnhookEvent(IEventSource* pSource) {
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&IEvents::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   // Create COM object
   CoInitialize(NULL);
   {
      IEventSource* pSource = 0;
      HRESULT hr = CoCreateInstance(__uuidof(CSource), NULL,         CLSCTX_ALL, __uuidof(IEventSource), (void **) &pSource);
      if (FAILED(hr)) {
         return -1;
      }

      // Create receiver and fire event
      CReceiver receiver;
      receiver.HookEvent(pSource);
      pSource->FireEvent();
      receiver.UnhookEvent(pSource);
   }
   CoUninitialize();
   return 0;
}
```

### <a name="output"></a>Output

```Output
MyHandler1 was called with value 123.
MyHandler2 was called with value 123.
```

## <a name="layout-dependent-com-events"></a><a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a>Eventos COM dependientes del diseño

La dependencia de diseño solo es un problema para la programación COM. En el control de eventos nativos y administrados, las firmas (tipo de valor devuelto, convención de llamada y argumentos) de los controladores deben coincidir con sus eventos, pero los nombres de controlador no tienen que coincidir con sus eventos.

Sin embargo, en el control de `event_receiver` eventos COM, cuando se establece el parámetro *layout_dependent* de **true**, se aplica la coincidencia de nombre y firma. Esto significa que los nombres y las firmas de los controladores del receptor de eventos deben coincidir exactamente con los nombres y las firmas de los eventos a los que están enlazados.

Cuando *layout_dependent* se establece en **false**, la convención de llamada y la clase de almacenamiento (virtual, estática, etc.) se pueden mezclar y combinar entre el método de evento de activación y los métodos de enlace (sus delegados). Es un poco más eficiente tener *layout_dependent*=**verdadero.**

Suponga, por ejemplo, que se define `IEventSource` para que tenga los siguientes métodos:

```cpp
[id(1)] HRESULT MyEvent1([in] int value);
[id(2)] HRESULT MyEvent2([in] int value);
```

Suponga que el origen de eventos tiene el siguiente formato:

```cpp
[coclass, event_source(com)]
class CSource : public IEventSource {
public:
   __event __interface IEvents;

   HRESULT FireEvent() {
      MyEvent1(123);
      MyEvent2(123);
      return S_OK;
   }
};
```

A continuación, en el receptor de eventos, cualquier controlador enlazado a un método en `IEventSource` debe coincidir con el nombre y la firma, de la manera siguiente:

```cpp
[coclass, event_receiver(com, true)]
class CReceiver {
public:
   HRESULT MyEvent1(int nValue) {  // name and signature matches MyEvent1
      ...
   }
   HRESULT MyEvent2(E c, char* pc) {  // signature doesn't match MyEvent2
      ...
   }
   HRESULT MyHandler1(int nValue) {  // name doesn't match MyEvent1 (or 2)
      ...
   }
   void HookEvent(IEventSource* pSource) {
      __hook(IFace, pSource);  // Hooks up all name-matched events
                               // under layout_dependent = true
      __hook(&IFace::MyEvent1, pSource, &CReceive::MyEvent1);   // valid
      __hook(&IFace::MyEvent2, pSource, &CSink::MyEvent2);   // not valid
      __hook(&IFace::MyEvent1, pSource, &CSink:: MyHandler1); // not valid
   }
};
```

## <a name="see-also"></a>Consulte también

[Manejo de eventos](../cpp/event-handling.md)
