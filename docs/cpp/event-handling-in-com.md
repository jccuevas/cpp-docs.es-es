---
title: "Control de eventos en COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM, eventos"
  - "declarar eventos"
  - "declarar eventos, control de eventos en COM"
  - "declarar eventos, en COM"
  - "controladores de eventos"
  - "controladores de eventos, COM"
  - "control de eventos"
  - "control de eventos, acerca del control de eventos"
  - "control de eventos, COM"
  - "receptores de eventos, en control de eventos"
  - "receptores de eventos, coincidencia de nombres y signatura"
  - "orígenes del evento, en control de eventos"
  - "enlazar eventos"
ms.assetid: 6b4617d4-a58e-440c-a8a6-1ad1c715b2bb
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de eventos en COM
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el control de eventos COM, puede configurar un origen de eventos y un receptor de eventos usando los atributos [event\_source](../windows/event-source.md) y [event\_receiver](../windows/event-receiver.md), respectivamente, que especifican `type`\=**com**.  Estos atributos insertan el código adecuado para las interfaces personalizadas, de envío y duales para permitir que las clases a las que se aplican desencadenen eventos y los controlen a través de puntos de conexión de COM.  
  
## Declarar eventos  
 En una clase de origen de eventos, use la palabra clave [\_\_event](../cpp/event.md) en una declaración de interfaz para declarar los métodos de esa interfaz como eventos.  Los eventos de esa interfaz se desencadenan cuando se llaman como métodos de interfaz.  Los métodos de las interfaces de eventos pueden tener cero o más parámetros \(que deben ser todos parámetros **in**\).  El tipo de valor devuelto puede ser void o cualquier tipo entero.  
  
## Definir controladores de eventos  
 En una clase de receptor de eventos, se definen los controladores de eventos, que son métodos con firmas \(tipos de valor devuelto, convenciones de llamada y argumentos\) que coinciden con el evento que van a controlar.  Para los eventos COM, las convenciones de llamada no tienen que coincidir; vea [Eventos COM dependientes del diseño](#vcconeventhandlingincomanchorlayoutdependentcomevents) más adelante para obtener información detallada.  
  
## Enlazar controladores de eventos a eventos  
 También en una clase de receptor de eventos, se usa la función intrínseca [\_\_hook](../cpp/hook.md) para asociar eventos a controladores de eventos y [\_\_unhook](../cpp/unhook.md) para desasociar eventos de los controladores de eventos.  Puede enlazar varios eventos a un controlador de eventos o varios controladores de eventos a un evento.  
  
> [!NOTE]
>  Normalmente, hay dos técnicas para permitir que un receptor de eventos COM acceda a las definiciones de interfaz del origen de eventos.  La primera, mostrada a continuación, es compartir un archivo de encabezado común.  La segunda es utilizar [\#import](../preprocessor/hash-import-directive-cpp.md) con el calificador de importación `embedded_idl`, para que la biblioteca de tipos del origen de eventos se escriba en el archivo .tlh con el código generado por el atributo.  
  
## Desencadenar eventos  
 Para desencadenar un evento, simplemente llame a un método de la interfaz declarado con la palabra clave `__event` en la clase del origen de eventos.  Si se han enlazado controladores al evento, se llamará a los controladores.  
  
### Código de eventos COM  
 En el ejemplo siguiente se muestra cómo desencadenar un evento en una clase COM.  Para compilar y ejecutar el ejemplo, consulte los comentarios del código.  
  
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
  
### Salida  
  
```  
MyHandler1 was called with value 123.  
MyHandler2 was called with value 123.  
```  
  
##  <a name="vcconeventhandlingincomanchorlayoutdependentcomevents"></a> Eventos COM dependientes del diseño  
 La dependencia de diseño solo es un problema para la programación COM.  En el control de eventos nativos y administrados, las firmas \(tipo de valor devuelto, convención de llamada y argumentos\) de los controladores deben coincidir con sus eventos, pero los nombres de controlador no tienen que coincidir con sus eventos.  
  
 Sin embargo, en el control de eventos COM, cuando se establece el parámetro *layout\_dependent* de **event\_receiver** en **true**, se aplica la coincidencia de nombre y firma.  Esto significa que los nombres y las firmas de los controladores del receptor de eventos deben coincidir exactamente con los nombres y las firmas de los eventos a los que están enlazados.  
  
 Cuando *layout\_dependent* se establece en **false**, la convención de llamada y la clase de almacenamiento \(virtual, estática, etc.\) se pueden combinar y corresponder entre el método de evento desencadenador y los métodos de enlace \(sus delegados\).  Esto es ligeramente más eficaz que establecer *layout\_dependent*\=**true**.  
  
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
  
## Vea también  
 [Control de eventos](../cpp/event-handling.md)