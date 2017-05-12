---
title: "Eventos (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
caps.latest.revision: 17
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 17
---
# Eventos (C++/CX)
Un tipo de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] puede declarar \(es decir, publicar\) eventos, y el código de cliente del mismo componente o de otros componentes puede suscribirse a esos eventos asociando métodos denominados *controladores de eventos* a dichos eventos. Se pueden asociar varios controladores de eventos a un único evento. Cuando el objeto de publicación genera el evento, hace que se invoquen todos los controladores de eventos. De esta manera, una clase de suscripción puede realizar la acción personalizada apropiada cuando el publicador genera el evento. Un evento tiene un tipo de delegado que especifica la signatura que deben tener todos los controladores de eventos para suscribirse al evento.  
  
## Usar eventos en componentes de Windows  
 Muchos componentes de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] exponen eventos. Por ejemplo, un objeto LightSensor desencadena un evento ReadingChanged cuando el sensor notifica un nuevo valor de luminiscencia. Si utilizas un objeto LightSensor en el programa, puedes definir un método al que se llamará cuando se desencadene el evento ReadingChanged. El método puede hacer todo lo que desees; el único requisito es que su signatura debe coincidir con la signatura del delegado. Para obtener más información sobre cómo crear un controlador de eventos de delegado y suscribirse a un evento, consulta [Delegados](../cppcx/delegates-c-cx.md).  
  
## Crear eventos personalizados  
  
### Declaración  
 Puedes declarar un evento en una clase ref o una interfaz, y este puede tener accesibilidad pública, interna \(pública o privada\), pública protegida, protegida, privada protegida o privada. Cuando se declara un evento, el compilador crea internamente un objeto que expone dos métodos de descriptor de acceso: add y remove. Cuando los objetos de suscripción registran controladores de eventos, el objeto de evento los almacena en una colección. Cuando se desencadena un evento, el objeto de evento invoca a su vez a todos los controladores de su lista. Un evento trivial, como el del siguiente ejemplo, tiene una memoria auxiliar implícita así como métodos implícitos de descriptor de acceso `add` y `remove`. También puedes especificar tus propios descriptores de acceso, del mismo modo que puedes especificar descriptores de acceso `get` y `set` personalizados en una propiedad.  La clase de implementación no puede completar un ciclo manualmente en la lista de suscriptores de eventos en un evento trivial.  
  
 En el ejemplo siguiente, se muestra cómo declarar y desencadenar un evento. Observa que el evento tiene un tipo delegado y se declara mediante el símbolo “^”.  
  
 [!code-cpp[cx_events#01](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/cx_events/class1.h#01)]  
  
### Uso  
 En el ejemplo siguiente se muestra cómo utiliza una clase de suscripción el operador `+=` para suscribirse al evento, y se proporciona un controlador de eventos que se invocará cuando se desencadene el evento. Observa que la función que se proporciona coincide con la firma del delegado que se define en el lado del publicador en el espacio de nombres `EventTest`.  
  
 [!code-cpp[cx_events#02](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/eventsupportinvs/eventclientclass.h#02)]  
  
> [!WARNING]
>  Normalmente es mejor utilizar una función con nombre, en lugar de una expresión lambda, para un controlador de eventos, a menos que tengas sumo cuidado para evitar referencias circulares. Una función con nombre captura el puntero "this" mediante referencia débil, mientras que una expresión lambda lo captura mediante referencia segura y crea una referencia circular. Para obtener más información, consulta [Referencias débiles e interrupción de ciclos \(C\+\+\/CX\)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).  
  
### Métodos add y remove personalizados  
 Internamente, un evento tiene un método add, un método remove y un método raise. Cuando el código de cliente se suscribe a un evento, se llama al método add y el delegado que se pasa se agrega a la lista de invocación del evento. La clase de publicación invoca el evento, hace que se llame al método raise\(\), y se llama a cada delegado de la lista a su vez. Un suscriptor puede quitarse de la lista de delegados, lo que hace que se llame al método remove del evento. El compilador proporciona versiones predeterminadas de estos métodos si no los defines en tu código; se conocen como eventos triviales. En muchos casos, un evento trivial es todo lo que se necesita.  
  
 Puedes especificar métodos add, remove y raise personalizados para un evento si tienes que realizar lógica personalizada en respuesta a la adición o eliminación de suscriptores. Por ejemplo, si tienes un objeto costoso que solo es necesario para la notificación de eventos, puedes diferir la creación del objeto hasta que un cliente se suscriba realmente al evento.  
  
 En el ejemplo siguiente se muestra cómo agregar métodos add, remove y raise personalizados a un evento:  
  
 [!code-cpp[cx_events#03](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/cx_events/class1.h#03)]  
  
## Quitar un controlador de eventos del suscriptor  
 Aunque no es muy frecuente, quizás desees quitar un controlador de eventos para un evento al que te suscribiste previamente. Por ejemplo, puedes desear sustituirlo por otro controlador de eventos o eliminar algunos recursos contenidos en él. Para quitar un controlador, debes almacenar el EventRegistrationToken que se devuelve de la operación `+=`. Puedes utilizar el operador `-=` en el token para quitar un controlador de eventos.  Sin embargo, el controlador original se podría seguir invocando incluso después haberse quitado. Por consiguiente, si deseas quitar un controlador de eventos, crea una marca de miembro y determina si se quita el evento y, a continuación, en el controlador de eventos, comprueba la marca y vuelve inmediatamente si se determina. En el ejemplo siguiente se muestra el patrón básico.  
  
 [!code-cpp[cx_events#04](../snippets/cpp/VS_Snippets_Misc/cx_events/cpp/eventsupportinvs/eventclientclass.h#04)]  
  
## Comentarios  
 Varios controladores se pueden asociar al mismo evento. El origen de eventos llama secuencialmente a todos los controladores de eventos del mismo subproceso. Si un receptor de eventos se bloquea dentro del método de controlador de eventos, impide que el origen de eventos invoque otros controladores de eventos para este evento.  
  
 El orden en que el origen de eventos invoca los controladores de eventos en los receptores de eventos no se garantiza y puede variar de una llamada a otra.  
  
## Vea también  
 [Sistema de tipos](../cppcx/type-system-c-cx.md)   
 [Delegados](../cppcx/delegates-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)