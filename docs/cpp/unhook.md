---
title: "__unhook | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__unhook"
  - "__unhook_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__unhook (palabra clave) [C++]"
  - "controladores de eventos, desasociar eventos"
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __unhook
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Disocia un método de control de un evento.  
  
## Sintaxis  
  
```  
  
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
  
#### Parámetros  
 **&** *SourceClass* `::` *EventMethod*  
 Un puntero al método de evento del que desenlaza el método de controlador de eventos:  
  
-   Eventos de C\+\+ nativo: *SourceClass* es la clase del origen de eventos e *EventMethod* es el evento.  
  
-   Eventos COM: *SourceClass* es la interfaz de origen de eventos e *EventMethod* es uno de sus métodos.  
  
-   Eventos administrados: *SourceClass* es la clase del origen de eventos e *EventMethod* es el evento.  
  
 `interface`  
 El nombre de interfaz que se va a desenlazar de `receiver`, solo para los receptores de eventos COM en los que el parámetro *layout\_dependent* del atributo [event\_receiver](../windows/event-receiver.md) es **true**.  
  
 *source*  
 Un puntero a una instancia del origen de eventos.  Dependiendo del `type` de código especificado en **event\_receiver**, *source* puede ser uno de:  
  
-   Un puntero nativo de objeto de origen de eventos.  
  
-   Un puntero basado en **IUnknown** \(origen COM\).  
  
-   Un puntero de objeto administrado \(para eventos administrados\).  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 Un puntero al método de controlador de eventos que se a desenlazar de un evento.  El controlador se especifica como un método de una clase o una referencia a la misma; si no se especifica el nombre de la clase, `__unhook` supone que la clase es aquella en que se llama.  
  
-   Eventos de C\+\+ nativo: *ReceiverClass* es la clase del receptor de eventos y `HandlerMethod` es el controlador.  
  
-   Eventos COM: *ReceiverClass* es la interfaz del receptor de eventos y `HandlerMethod` es uno de sus controladores.  
  
-   Eventos administrados: *ReceiverClass* es la clase del receptor de eventos y `HandlerMethod` es el controlador.  
  
 `receiver` \(opcional\)  
 Un puntero a una instancia de la clase del receptor de eventos.  Si no se especifica un receptor, el valor predeterminado es la estructura o clase del receptor en que se llama a `__unhook`.  
  
## Uso  
 Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.  
  
## Comentarios  
 Utilice la función intrínseca `__unhook` en un receptor de eventos para desasociar o "desenlazar" un método de controlador de un método de evento.  
  
 Hay tres formas de `__unhook`.  Puede usar la primera forma \(cuatro argumento\) en la mayoría de los casos.  Puede usar la segunda forma \(dos argumentos\) de `__unhook` solo para un receptor de eventos COM; de este modo se desenlaza la interfaz de eventos completa.  Puede utilizar la tercera forma \(un argumento\) para desenlazar todos los delegados del origen especificado.  
  
 Un valor devuelto distinto de cero indica que se ha producido un error \(los eventos administrados producirán una excepción\).  
  
 Si se llama a `__unhook` en un evento y un controlador de eventos que ya no están enlazados, no tendrá efecto.  
  
 En tiempo de compilación, el compilador comprueba que el evento existe y realiza la comprobación de tipo de parámetros con el controlador especificado.  
  
 Con excepción de eventos COM, se puede llamar a `__hook` y `__unhook` fuera del receptor de eventos.  
  
 Una alternativa al uso de `__unhook` es utilizar el operador \-\=.  
  
 Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, vea [event](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## Ejemplo  
 Vea [Control de eventos en C\+\+ nativo](../cpp/event-handling-in-native-cpp.md) y [Control de eventos en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_event](../cpp/event.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_raise](../cpp/raise.md)