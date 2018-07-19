---
title: __unhook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __unhook
- __unhook_cpp
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], dissociating events
- __unhook keyword [C++]
ms.assetid: 953a14f3-5199-459d-81e5-fcf015a19878
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 069d206418fd392e28114d977b3448f8306a3119
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944781"
---
# <a name="unhook"></a>__unhook
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
 **&** *SourceClass* `::` *EventMethod*  
 Un puntero al método de evento del que desenlaza el método de controlador de eventos:  
  
-   Eventos de C++ nativo: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.  
  
-   Eventos COM: *SourceClass* es la interfaz de origen de eventos y *EventMethod* es uno de sus métodos.  
  
-   Eventos administrados: *SourceClass* es la clase de origen de eventos y *EventMethod* es el evento.  
  
 *interface*  
 El nombre de la interfaz que se va a Desenlazar de *receptor*, solo para los receptores de eventos COM en el que el *layout_dependent* parámetro de la [event_receiver](../windows/event-receiver.md) atributo es **true**.  
  
 *source*  
 Un puntero a una instancia del origen de eventos. Según el código de `type` especificado en **event_receiver**, *origen* puede ser uno de los siguientes:  
  
-   Un puntero nativo de objeto de origen de eventos.  
  
-   Un **IUnknown**-en función de puntero (origen COM).  
  
-   Un puntero de objeto administrado (para eventos administrados).  
  
 **&** *ReceiverClass* `::` `HandlerMethod`  
 Un puntero al método de controlador de eventos que se a desenlazar de un evento. El controlador se especifica como un método de una clase o una referencia a la misma; Si no especifica el nombre de clase, **__unhook** se da por supuesto que en el que se llama la clase.  
  
-   Eventos de C++ nativo: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.  
  
-   Eventos COM: *ReceiverClass* es la interfaz de receptor de eventos y `HandlerMethod` es uno de sus controladores.  
  
-   Eventos administrados: *ReceiverClass* es la clase de receptor de eventos y `HandlerMethod` es el controlador.  
  
 *receptor*(opcional)  
 Un puntero a una instancia de la clase del receptor de eventos. Si no especifica un receptor, el valor predeterminado es la clase del receptor o estructura en la que **__unhook** se llama.  
  
## <a name="usage"></a>Uso  
 Se puede usar en cualquier ámbito de función, incluida main, fuera de la clase del receptor de eventos.  
  
## <a name="remarks"></a>Comentarios  
 Utilice la función intrínseca **__unhook** en un receptor de eventos para desasociar o "desenlazar" un método de controlador de un método de evento.  
  
 Hay tres formas de **__unhook**. Puede usar la primera forma (cuatro argumento) en la mayoría de los casos. Puede usar la segunda forma (dos argumentos) de **__unhook** solo para un receptor de eventos COM; este modo desenlaza la interfaz de eventos completa. Puede utilizar la tercera forma (un argumento) para desenlazar todos los delegados del origen especificado.  
  
 Un valor devuelto distinto de cero indica que se ha producido un error (los eventos administrados producirán una excepción).  
  
 Si se llama a **__unhook** en un evento y el controlador de eventos que ya no están enlazados, no tendrá ningún efecto.  
  
 En tiempo de compilación, el compilador comprueba que el evento existe y realiza la comprobación de tipo de parámetros con el controlador especificado.  
  
 A excepción de los eventos COM, **__hook** y **__unhook** puede llamarse fuera del receptor de eventos.  
  
 Una alternativa al uso **__unhook** consiste en usar el operador-=.  
  
 Para obtener información sobre la codificación de eventos administrados en la nueva sintaxis, vea [eventos](../windows/event-cpp-component-extensions.md).  
  
> [!NOTE]
>  Una clase o struct basada en plantilla no puede contener eventos.  
  
## <a name="example"></a>Ejemplo  
 Consulte [control de eventos en C++ nativo](../cpp/event-handling-in-native-cpp.md) y [control de eventos en COM](../cpp/event-handling-in-com.md) para obtener ejemplos.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [event_source](../windows/event-source.md)   
 [event_receiver](../windows/event-receiver.md)   
 [__event](../cpp/event.md)   
 [__hook](../cpp/hook.md)   
 [__raise](../cpp/raise.md)