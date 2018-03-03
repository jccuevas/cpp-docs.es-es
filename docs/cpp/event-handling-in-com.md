---
title: Control de eventos en COM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1c57b8429a05ab3989dce318f4c16a58475560a1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="event-handling-in-com"></a>Control de eventos en COM
En el control de eventos COM, configurar un receptor de origen y de evento de eventos mediante el [event_source](../windows/event-source.md) y [event_receiver](../windows/event-receiver.md) atributos, respectivamente, especificando `type` = **com**. Estos atributos insertan el código adecuado para las interfaces personalizadas, de envío y duales para permitir que las clases a las que se aplican desencadenen eventos y los controlen a través de puntos de conexión de COM.  
  
## <a name="declaring-events"></a>Declarar eventos  
 En una clase de origen de eventos, use la [__event](../cpp/event.md) palabra clave en una declaración de interfaz para declarar los métodos de esa interfaz como eventos. Los eventos de esa interfaz se desencadenan cuando se llaman como métodos de interfaz. Los métodos de interfaces de eventos pueden tener cero o más parámetros (que deben ser todos **en** parámetros). El tipo de valor devuelto puede ser void o cualquier tipo entero.  
  
## <a name="defining-event-handlers"></a>Definir controladores de eventos  
 En una clase de receptor de eventos, se definen los controladores de eventos, que son métodos con firmas (tipos de valor devuelto, convenciones de llamada y argumentos) que coinciden con el evento que van a controlar. Para los eventos COM, convenciones de llamada no tiene que coincidir; vea [eventos COM dependientes del diseño](#vcconeventhandlingincomanchorlayoutdependentcomevents) a continuación para obtener más información.  
  
## <a name="hooking-event-handlers-to-events"></a>Enlazar controladores de eventos a eventos  
 También en una clase de receptor de eventos, use la función intrínseca [__hook](../cpp/hook.md) para asociar eventos a controladores de eventos y [__unhook](../cpp/unhook.md) para desasociar eventos de los controladores de eventos. Puede enlazar varios eventos a un controlador de eventos o varios controladores de eventos a un evento.  
  
> [!NOTE]
>  Normalmente, hay dos técnicas para permitir que un receptor de eventos COM acceda a las definiciones de interfaz del origen de eventos. La primera, mostrada a continuación, es compartir un archivo de encabezado común. El segundo consiste en usar [#import](../preprocessor/hash-import-directive-cpp.md) con el `embedded_idl` importar calificador, por lo que la biblioteca de tipos de origen de eventos se escribe en el archivo .tlh con el código generado por el atributo.  
  
## <a name="firing-events"></a>Desencadenar eventos  
 Para desencadenar un evento, simplemente llame a un método de la interfaz declarado con la palabra clave `__event` en la clase del origen de eventos. Si se han enlazado controladores al evento, se llamará a los controladores.  
  
### <a name="com-event-code"></a>Código de eventos COM  
 En el ejemplo siguiente se muestra cómo desencadenar un evento en una clase COM. Para compilar y ejecutar el ejemplo, consulte los comentarios del código.  
  
```  
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
  
```  
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
  
```  
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
  
### <a name="output"></a>Salida  
  
```  
MyHandler1 was called with value 123.  
MyHandler2 was called with value 123.  
```  
  
##  <a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a>Eventos COM dependientes del diseño  
 La dependencia de diseño solo es un problema para la programación COM. En el control de eventos nativos y administrados, las firmas (tipo de valor devuelto, convención de llamada y argumentos) de los controladores deben coincidir con sus eventos, pero los nombres de controlador no tienen que coincidir con sus eventos.  
  
 Sin embargo, en el control de eventos de COM, al establecer el *layout_dependent* parámetro de **event_receiver** a **true**, se aplica la coincidencia de nombre y firma. Esto significa que los nombres y las firmas de los controladores del receptor de eventos deben coincidir exactamente con los nombres y las firmas de los eventos a los que están enlazados.  
  
 Cuando *layout_dependent* está establecido en **false**, la clase que realiza la llamada convención y almacenamiento (virtual, estática etc.) se puede combinar y corresponder entre el desencadenamiento de método de evento y los métodos de enlace (sus delegados). Es algo más eficaz tener *layout_dependent*=**true**.  
  
 Suponga, por ejemplo, que se define `IEventSource` para que tenga los siguientes métodos:  
  
```  
[id(1)] HRESULT MyEvent1([in] int value);  
[id(2)] HRESULT MyEvent2([in] int value);  
```  
  
 Suponga que el origen de eventos tiene el siguiente formato:  
  
```  
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
  
```  
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
  
## <a name="see-also"></a>Vea también  
 [Control de eventos](../cpp/event-handling.md)