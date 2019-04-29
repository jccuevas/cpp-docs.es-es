---
title: Eventos (C++/CX)
ms.date: 01/22/2017
ms.assetid: 31c8e08a-00ad-40f9-8f7e-124864aaad58
ms.openlocfilehash: 8e7e8616831e66a7f59ed849fc92ef2553aadb5b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301544"
---
# <a name="events-ccx"></a>Eventos (C++/CX)

Puede declarar el tipo de un Runtime de Windows (que es, publicar) eventos y el código de cliente en el mismo componente o de otros componentes pueden suscribirse a esos eventos asociando métodos denominados *controladores de eventos* con el evento. Se pueden asociar varios controladores de eventos a un único evento. Cuando el objeto de publicación genera el evento, hace que se invoquen todos los controladores de eventos. De esta manera, una clase de suscripción puede realizar la acción personalizada apropiada cuando el publicador genera el evento. Un evento tiene un tipo de delegado que especifica la signatura que deben tener todos los controladores de eventos para suscribirse al evento.

## <a name="consuming-events-in-windows-components"></a>Usar eventos en componentes de Windows

Muchos componentes en tiempo de ejecución de Windows exponen eventos. Por ejemplo, un objeto LightSensor desencadena un evento ReadingChanged cuando el sensor notifica un nuevo valor de luminiscencia. Si utilizas un objeto LightSensor en el programa, puedes definir un método al que se llamará cuando se desencadene el evento ReadingChanged. El método puede hacer lo que quiera hacer; el único requisito es que su firma debe coincidir con la firma del delegado que para obtener más información acerca de cómo crear un controlador de eventos de delegado y suscribirse a un evento, vea [delegados](../cppcx/delegates-c-cx.md).

## <a name="creating-custom-events"></a>Crear eventos personalizados

### <a name="declaration"></a>Declaración

Puedes declarar un evento en una clase ref o una interfaz, y este puede tener accesibilidad pública, interna (pública o privada), pública protegida, protegida, privada protegida o privada. Cuando se declara un evento, el compilador crea internamente un objeto que expone dos métodos de descriptor de acceso: add y remove. Cuando los objetos de suscripción registran controladores de eventos, el objeto de evento los almacena en una colección. Cuando se desencadena un evento, el objeto de evento invoca a su vez a todos los controladores de su lista. Un evento trivial, como el del siguiente ejemplo, tiene una memoria auxiliar implícita así como métodos implícitos de descriptor de acceso `add` y `remove` . También puedes especificar tus propios descriptores de acceso, del mismo modo que puedes especificar descriptores de acceso `get` y `set` personalizados en una propiedad.  La clase de implementación no puede completar un ciclo manualmente en la lista de suscriptores de eventos en un evento trivial.

En el ejemplo siguiente, se muestra cómo declarar y desencadenar un evento. Observa que el evento tiene un tipo delegado y se declara mediante el símbolo “^”.

[!code-cpp[cx_events#01](../cppcx/codesnippet/CPP/cx_events/class1.h#01)]

### <a name="usage"></a>Uso

En el ejemplo siguiente se muestra cómo utiliza una clase de suscripción el operador `+=` para suscribirse al evento, y se proporciona un controlador de eventos que se invocará cuando se desencadene el evento. Observa que la función que se proporciona coincide con la firma del delegado que se define en el lado del publicador en el espacio de nombres `EventTest` .

[!code-cpp[cx_events#02](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#02)]

> [!WARNING]
> Normalmente es mejor utilizar una función con nombre, en lugar de una expresión lambda, para un controlador de eventos, a menos que tengas sumo cuidado para evitar referencias circulares. Una función con nombre captura el puntero "this" mediante referencia débil, mientras que una expresión lambda lo captura mediante referencia segura y crea una referencia circular. Para obtener más información, consulta [Referencias débiles e interrupción de ciclos (C++/CX)](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

### <a name="custom-add-and-remove-methods"></a>Métodos add y remove personalizados

Internamente, un evento tiene un método add, un método remove y un método raise. Cuando el código de cliente se suscribe a un evento, se llama al método add y el delegado que se pasa se agrega a la lista de invocación del evento. La clase de publicación invoca el evento, hace que se llame al método raise(), y se llama a cada delegado de la lista a su vez. Un suscriptor puede quitarse de la lista de delegados, lo que hace que se llame al método remove del evento. El compilador proporciona versiones predeterminadas de estos métodos si no los defines en tu código; se conocen como eventos triviales. En muchos casos, un evento trivial es todo lo que se necesita.

Puedes especificar métodos add, remove y raise personalizados para un evento si tienes que realizar lógica personalizada en respuesta a la adición o eliminación de suscriptores. Por ejemplo, si tienes un objeto costoso que solo es necesario para la notificación de eventos, puedes diferir la creación del objeto hasta que un cliente se suscriba realmente al evento.

En el ejemplo siguiente se muestra cómo agregar métodos add, remove y raise personalizados a un evento:

[!code-cpp[cx_events#03](../cppcx/codesnippet/CPP/cx_events/class1.h#03)]

## <a name="removing-an-event-handler-from-the-subscriber-side"></a>Quitar un controlador de eventos del suscriptor

Aunque no es muy frecuente, quizás desees quitar un controlador de eventos para un evento al que te suscribiste previamente. Por ejemplo, puedes desear sustituirlo por otro controlador de eventos o eliminar algunos recursos contenidos en él. Para quitar un controlador, debes almacenar el EventRegistrationToken que se devuelve de la operación `+=` . Puedes utilizar el operador `-=` en el token para quitar un controlador de eventos.  Sin embargo, el controlador original se podría seguir invocando incluso después haberse quitado. Por consiguiente, si deseas quitar un controlador de eventos, crea una marca de miembro y determina si se quita el evento y, a continuación, en el controlador de eventos, comprueba la marca y vuelve inmediatamente si se determina. En el ejemplo siguiente se muestra el patrón básico.

[!code-cpp[cx_events#04](../cppcx/codesnippet/CPP/eventsupportinvs/eventclientclass.h#04)]

### <a name="remarks"></a>Comentarios

Varios controladores se pueden asociar al mismo evento. El origen de eventos llama secuencialmente a todos los controladores de eventos del mismo subproceso. Si un receptor de eventos se bloquea dentro del método de controlador de eventos, impide que el origen de eventos invoque otros controladores de eventos para este evento.

El orden en que el origen de eventos invoca los controladores de eventos en los receptores de eventos no se garantiza y puede variar de una llamada a otra.

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Delegados](../cppcx/delegates-c-cx.md)<br/>
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)
