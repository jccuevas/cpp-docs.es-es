---
title: __hook | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __hook
dev_langs:
- C++
helpviewer_keywords:
- __hook keyword [C++]
- event handlers, connecting events to
ms.assetid: f4cabb10-d293-4c0e-a1d2-4745ef9cc22c
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 21bb75853d8664ad46bc48fc907946ae5a147f9a
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

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
  
#### <a name="parameters"></a>Parámetros  
 **&***SourceClass* `::` *EventMethod*  
 Un puntero al método de evento al que se enlaza el método de controlador de eventos:  
  
-   Eventos de C++ nativo: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.  
  
-   Eventos COM: *SourceClass* es la interfaz de origen de eventos y *EventMethod* es uno de sus métodos.  
  
-   Eventos administrados: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.  
  
 `interface`  
 El nombre de la interfaz que se va a enlazar a `receiver`, solo para los receptores de eventos COM en el que el *layout_dependent* parámetro de la [event_receiver](../windows/event-receiver.md) atributo es **true**.  
  
 *origen*  
 Un puntero a una instancia del origen de eventos. Según el código de `type` especificado en **event_receiver**, *origen* puede ser uno de los siguientes:  
  
-   Un puntero nativo de objeto de origen de eventos.  
  
-   Un **IUnknown**-en función de puntero (origen COM).  
  
-   Un puntero de objeto administrado (para eventos administrados).  
  
 **&***ReceiverClass* `::``HandlerMethod`  
 Un puntero al método de controlador de eventos que se a enlazar a un evento. El controlador se especifica como un método de una clase o una referencia a la misma; si no se especifica el nombre de la clase, `__hook` supone que la clase es aquella en que se llama.  
  
-   Eventos de C++ nativo: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.  
  
-   Eventos COM: *ReceiverClass* es la interfaz de receptor de eventos y `HandlerMethod` es uno de sus controladores.  
  
-   Eventos administrados: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.  
  
 `receiver`(opcional)  
 Un puntero a una instancia de la clase del receptor de eventos. Si no se especifica un receptor, el valor predeterminado es la estructura o clase del receptor en que se llama a `__hook`.  
  
## <a name="usage"></a>Uso  
 Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.  
  
## <a name="remarks"></a>Comentarios  
 Utilice la función intrínseca `__hook` en un receptor de eventos para asociar o enlazar un método de controlador con un método de evento. Después se llama al controlador especificado cuando el origen provoca el evento especificado. Puede enlazar varios controladores a un único evento o enlazar varios eventos a un único controlador.  
  
 Hay dos formas de `__hook`. Puede usar la primera forma (cuatro argumento) en la mayoría de los casos, concretamente, para los receptores de eventos COM en el que el *layout_dependent* parámetro de la [event_receiver](../windows/event-receiver.md) atributo es **false **.  
  
 En estos casos no necesita enlazar todos los métodos en una interfaz antes de desencadenar un evento en uno de los métodos; solo debe enlazarse el método que controlará el evento. Puede usar la segunda forma (dos argumentos) de `__hook` solo para un receptor de eventos COM en el que *layout_dependent***= true**.  
  
 `__hook` devuelve un valor de tipo long. Un valor devuelto distinto de cero indica que se ha producido un error (los eventos administrados producirán una excepción).  
  
 El compilador comprueba la existencia de un evento y que la firma del evento coincida con la firma del delegado.  
  
 Con excepción de eventos COM, se puede llamar a `__hook` y `__unhook` fuera del receptor de eventos.  
  
 Una alternativa al uso de `__hook` es utilizar el operador +=.  
  
 Para obtener información sobre los eventos administrados en la nueva sintaxis de codificación, vea [eventos](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## <a name="example"></a>Ejemplo  
 Vea [control de eventos en C++ nativo](../cpp/event-handling-in-native-cpp.md) y [control de eventos en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Control de eventos](../cpp/event-handling.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__unhook](../cpp/unhook.md)   
 [__raise](../cpp/raise.md)
