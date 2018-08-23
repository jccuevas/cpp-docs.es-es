---
title: Event (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event
- event_cpp
dev_langs:
- C++
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0be744b8f703bfdc6487995e4a082e5b4c1561c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606845"
---
# <a name="event--c-component-extensions"></a>event (Extensiones de componentes de C++)

El **eventos** palabra clave declara una *eventos*, que es una notificación a los suscriptores registrados (*controladores de eventos*) que ha sucedido algo de interés.

## <a name="all-runtimes"></a>Todos los runtimes

C++ / c++ / CX admite la declaración de un *miembro de evento* o un *bloque de eventos*. Un miembro de evento es una forma abreviada para declarar un bloque de eventos. De forma predeterminada, un miembro de evento declara las funciones `add()`, `remove()`, y `raise()` declaradas explícitamente en un bloque de eventos. Para personalizar las funciones de un miembro de evento, declare un bloque de eventos en su lugar y, a continuación, reemplace las funciones que necesite.

### <a name="syntax"></a>Sintaxis

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parámetros

*Modificador*  
Un modificador que se puede utilizar en la declaración de evento o un método de descriptor de acceso de eventos.  Los valores posibles son **estático** y **virtual**.

*delegate*  
El [delegar](../windows/delegate-cpp-component-extensions.md), cuya firma debe coincidir con el controlador de eventos.

*event_name*  
Nombre del evento.

*RETURN_VALUE*  
El valor devuelto del método de descriptor de acceso del evento.  Para que sea comprobable, el tipo devuelto debe ser **void**.

*Parámetros*  
(opcional) Parámetros para el `raise` método, que coincide con la firma de la *delegar* parámetro.

### <a name="remarks"></a>Comentarios

Un evento es una asociación entre un delegado (delegate) y una función miembro (controlador de eventos) que responde a la activación del evento y permite a los clientes de cualquier clase registrar los métodos que cumplen con la firma y tipo de valor devuelto del delegado (delegate) subyacente.

Hay dos tipos de declaraciones de eventos:

*miembro de datos de evento*  
El compilador crea automáticamente almacenamiento para el evento en el formulario de un miembro del tipo delegate y crea funciones miembro internas `add()`, `remove()`, y `raise()` . Un miembro de datos de evento debe declararse dentro de una clase. El tipo de valor devuelto del tipo de valor devuelto del delegado debe coincidir con el tipo de valor devuelto del controlador de eventos.

*bloque de eventos*  
Un bloque de eventos le permite personalizar y declarar explícitamente el comportamiento de los métodos `add()`, `remove()`, y `raise()`.

Puede usar **operadores +=** y **operador-=** para agregar y quitar un evento de controlador o llame a la `add()` y `remove()` métodos explícitamente.

**evento** es una palabra clave contextual; consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [eventos (C++ / c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx).

Si desea agregar y, a continuación, quitar un controlador de eventos, debe guardar la estructura EventRegistrationToken devuelta por la operación de adición. A continuación, en la operación de eliminación, debe utilizar la estructura guardada EventRegistrationToken para identificar el controlador de eventos que se va a eliminar.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

El **eventos** palabra clave le permite declarar un evento. Un evento es una forma que tiene una clase para proporcionar notificaciones cuando ocurre algo de interés.

### <a name="syntax"></a>Sintaxis

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Parámetros

*Modificador*  
Un modificador que se puede utilizar en la declaración de evento o un método de descriptor de acceso de eventos.  Los valores posibles son **estático** y **virtual**.

*delegate*  
El [delegar](../windows/delegate-cpp-component-extensions.md), cuya firma debe coincidir con el controlador de eventos.

*event_name*  
Nombre del evento.

*RETURN_VALUE*  
El valor devuelto del método de descriptor de acceso del evento.  Para que sea comprobable, el tipo devuelto debe ser **void**.

*Parámetros*  
(opcional) Parámetros para el `raise` método, que coincide con la firma de la *delegar* parámetro.

### <a name="remarks"></a>Comentarios

Un evento es una asociación entre un delegado (delegate) y una función miembro (controlador de eventos) que responde a la activación del evento y permite a los clientes de cualquier clase registrar los métodos que cumplen con la firma y tipo de valor devuelto del delegado (delegate) subyacente.

El delegado (delegate) puede tener uno o varios métodos asociados que se llamarán cuando su código indique que se ha producido el evento. Un evento de un programa puede estar disponible para otros programas diseñados para Common Language Runtime de .NET Framework .

Hay dos tipos de declaraciones de eventos:

*miembros de datos de evento*  
El compilador para eventos de miembro de datos crea el almacenamiento para el evento en forma de un miembro del tipo delegate.  Un miembro de datos de evento debe declararse dentro de una clase. Esto también se conoce como un evento trivial (vea el siguiente ejemplo de código).

*bloques de eventos*  
Los bloques de eventos le permiten personalizar el comportamiento de los métodos add, remove y raise mediante su implementación. La firma de los métodos add, remove y raise debe coincidir con la firma del delegado (delegate).  Los eventos del bloque de eventos no son miembros de datos y cualquier uso como un miembro de datos generará un error del compilador.

El tipo de valor devuelto del controlador de eventos debe coincidir con el del delegado.

En .NET Framework, puede tratar un miembro de datos como si se tratara de un método en sí mismo (es decir, el método `Invoke` de su delegado correspondiente). Debe predefinir el tipo de delegado para declarar un miembro de datos de evento administrado. En cambio, un método de evento administrado define implícitamente el delegado administrado correspondiente si todavía no se ha definido.  Dispone de un ejemplo de código al final de este tema.

Al declarar un evento administrado, puede especificar que se agreguen y quiten los descriptores de acceso a los que se llamará cuando se agreguen o quiten los controladores de eventos mediante los operadores += y -=. Los métodos add, remove y raise pueden llamarse de forma explícita.

A continuación se indican los pasos para crear y utilizar eventos en Visual C++:

1. Cree o identifique a un delegado (delegate). Si va a definir su propio evento, también debe asegurarse de que hay un delegado que se va a usar con el **eventos** palabra clave. Si el evento está predefinido, en .NET Framework, por ejemplo, entonces los consumidores del evento solo necesitan conocer el nombre del delegado.

2. Cree una clase que contenta:

   - Un evento creado desde el delegado (delegate).

   - (opcional) Un método que comprueba que una instancia del delegado declarado con el **eventos** palabra clave existe. De lo contrario, esta lógica debe colocarse en el código que desencadena el evento.

   - Métodos que llaman al evento. Estos métodos pueden ser reemplazos de alguna funcionalidad de la clase base.

   Esta clase define el evento.

3. Defina una o más clases que conecte los métodos con el evento. Cada una de estas clases se asociará a uno o más métodos con el evento de la clase base.

4. Utilice el evento:

   - Cree un objeto de la clase que contenga la declaración del evento.

   - Cree un objeto de la clase que contenga la definición del evento.

Para obtener más información sobre C + + / eventos de la CLI, consulte

- [Eventos de una interfaz](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

El ejemplo de código siguiente demuestra la declaración de pares de delegados, eventos y controladores de eventos; suscribir (agregar) los controladores de eventos; invocar los controladores de eventos; y, a continuación, cancelar la suscripción (eliminar) de los controladores de eventos.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

El ejemplo de código siguiente demuestra la lógica utilizada para generar el método `raise` de un evento trivial: si el evento tiene uno o varios suscriptores, llamar al método `raise` llama implícita o explícitamente al delegado (delegate). Si el valor devuelto del delegado tipo no es **void** y si no hay ningún suscriptor de eventos, el `raise` método devuelve el valor predeterminado para el tipo de delegado. Si no hay ningún suscriptor de eventos, llamar al método `raise` simplemente devuelve y no se genera ninguna excepción. Si el delegado devuelve no es de tipo **void**, se devuelve el tipo de delegado.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)