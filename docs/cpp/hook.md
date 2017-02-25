---
title: "__hook | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__hook_cpp"
  - "__hook"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__hook (palabra clave) [C++]"
  - "controladores de eventos, conectar eventos"
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __hook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asocia un método de control a un evento.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 **&** *SourceClass* `::` *EventMethod*  
 Un puntero al método de evento al que se enlaza el método de controlador de eventos:  
  
-   Eventos de C\+\+ nativo: *SourceClass* es la clase del origen de eventos e *EventMethod* es el evento.  
  
-   Eventos COM: *SourceClass* es la interfaz de origen de eventos e *EventMethod* es uno de sus métodos.  
  
-   Eventos administrados: *SourceClass* es la clase del origen de eventos e *EventMethod* es el evento.  
  
 `interface`  
 El nombre de interfaz que se va a enlazar a `receiver`, solo para los receptores de eventos COM en los que el parámetro *layout\_dependent* del atributo [event\_receiver](../windows/event-receiver.md) es **true**.  
  
 *source*  
 Un puntero a una instancia del origen de eventos.  Dependiendo del `type` de código especificado en **event\_receiver**, *source* puede ser uno de:  
  
-   Un puntero nativo de objeto de origen de eventos.  
  
-   Un puntero basado en **IUnknown** \(origen COM\).  
  
-   Un puntero de objeto administrado \(para eventos administrados\).  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 Un puntero al método de controlador de eventos que se a enlazar a un evento.  El controlador se especifica como un método de una clase o una referencia a la misma; si no se especifica el nombre de la clase, `__hook` supone que la clase es aquella en que se llama.  
  
-   Eventos de C\+\+ nativo: *ReceiverClass* es la clase del receptor de eventos y `HandlerMethod` es el controlador.  
  
-   Eventos COM: *ReceiverClass* es la interfaz del receptor de eventos y `HandlerMethod` es uno de sus controladores.  
  
-   Eventos administrados: *ReceiverClass* es la clase del receptor de eventos y `HandlerMethod` es el controlador.  
  
 `receiver` \(opcional\)  
 Un puntero a una instancia de la clase del receptor de eventos.  Si no se especifica un receptor, el valor predeterminado es la estructura o clase del receptor en que se llama a `__hook`.  
  
## Uso  
 Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.  
  
## Comentarios  
 Utilice la función intrínseca `__hook` en un receptor de eventos para asociar o enlazar un método de controlador con un método de evento.  Después se llama al controlador especificado cuando el origen provoca el evento especificado.  Puede enlazar varios controladores a un único evento o enlazar varios eventos a un único controlador.  
  
 Hay dos formas de `__hook`.  Puede usar el primer formulario \(de cuatro argumentos\) en la mayoría de los casos, concretamente, para los receptores de eventos COM en los que el parámetro *layout\_dependent* de [event\_receiver](../windows/event-receiver.md) es **false**.  
  
 En estos casos no necesita enlazar todos los métodos en una interfaz antes de desencadenar un evento en uno de los métodos; solo debe enlazarse el método que controlará el evento.  Puede usar el segundo formulario \(de dos argumentos\) de `__hook` solo para un receptor de eventos COM en el que *layout\_dependent* es **\=true**.  
  
 `__hook` devuelve un valor de tipo long.  Un valor devuelto distinto de cero indica que se ha producido un error \(los eventos administrados producirán una excepción\).  
  
 El compilador comprueba la existencia de un evento y que la firma del evento coincida con la firma del delegado.  
  
 Con excepción de eventos COM, se puede llamar a `__hook` y `__unhook` fuera del receptor de eventos.  
  
 Una alternativa al uso de `__hook` es utilizar el operador \+\=.  
  
 Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, vea [event](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## Ejemplo  
 Vea [Control de eventos en C\+\+ nativo](../cpp/event-handling-in-native-cpp.md) y [Control de eventos en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Control de eventos](../cpp/event-handling.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [\_\_raise](../cpp/raise.md)