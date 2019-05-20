---
title: event (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 26bfc3bb9892486353f55a71cfd86a17f2de98b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516590"
---
# <a name="event--ccli-and-ccx"></a>event (C++/CLI y C++/CX)

La palabra clave **event** declara un *evento*, que es una notificación a los suscriptores registrados (*controladores de eventos*) de que se ha producido algo de interés.

## <a name="all-runtimes"></a>Todos los runtimes

C++/CX admite la declaración de un *miembro de evento* o un *bloque de eventos*. Un miembro de evento es una forma abreviada para declarar un bloque de eventos. De forma predeterminada, un miembro de evento declara las funciones `add()`, `remove()`, y `raise()` declaradas explícitamente en un bloque de eventos. Para personalizar las funciones de un miembro de evento, declare un bloque de eventos en su lugar y, a continuación, reemplace las funciones que necesite.

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

*modifier*<br/>
Un modificador que se puede utilizar en la declaración de evento o un método de descriptor de acceso de eventos.  Los valores posibles son **static** y **virtual**.

*delegate*<br/>
Delegado ([delegate](delegate-cpp-component-extensions.md)), cuya firma debe coincidir con la del controlador de eventos.

*event_name*<br/>
Nombre del evento.

*return_value*<br/>
El valor devuelto del método de descriptor de acceso del evento.  Para que sea comprobable, el tipo devuelto debe ser **void**.

*parameters*<br/>
(opcional) Parámetros para el método `raise`, que coincide con la firma del parámetro *delegate*.

### <a name="remarks"></a>Comentarios

Un evento es una asociación entre un delegado (delegate) y una función miembro (controlador de eventos) que responde a la activación del evento y permite a los clientes de cualquier clase registrar los métodos que cumplen con la firma y devuelven el tipo de delegado subyacente.

Hay dos tipos de declaraciones de eventos:

*miembro de datos de evento*<br/>
El compilador crea automáticamente almacenamiento para el evento en el formulario de un miembro del tipo delegate y crea funciones miembro internas `add()`, `remove()`, y `raise()` . Un miembro de datos de evento debe declararse dentro de una clase. El tipo de valor devuelto del tipo de valor devuelto del delegado debe coincidir con el tipo de valor devuelto del controlador de eventos.

*bloque de eventos*<br/>
Un bloque de eventos le permite personalizar y declarar explícitamente el comportamiento de los métodos `add()`, `remove()`, y `raise()`.

Puede utilizar **operators+=** y **operator-=** para agregar y quitar un controlador de eventos, o llamar a los métodos `add()` y `remove()` explícitamente.

**event** es una palabra clave contextual; para obtener más información, consulte [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) (Palabras clave contextuales).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Eventos (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755799.aspx).

Si desea agregar y, a continuación, quitar un controlador de eventos, debe guardar la estructura EventRegistrationToken devuelta por la operación de adición. A continuación, en la operación de eliminación, debe utilizar la estructura guardada EventRegistrationToken para identificar el controlador de eventos que se va a eliminar.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

La palabra clave **event** le permite declarar un evento. Un evento es una forma que tiene una clase para proporcionar notificaciones cuando ocurre algo de interés.

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

*modifier*<br/>
Un modificador que se puede utilizar en la declaración de evento o un método de descriptor de acceso de eventos.  Los valores posibles son **static** y **virtual**.

*delegate*<br/>
Delegado ([delegate](delegate-cpp-component-extensions.md)), cuya firma debe coincidir con la del controlador de eventos.

*event_name*<br/>
Nombre del evento.

*return_value*<br/>
El valor devuelto del método de descriptor de acceso del evento.  Para que sea comprobable, el tipo devuelto debe ser **void**.

*parameters*<br/>
(opcional) Parámetros para el método `raise`, que coincide con la firma del parámetro *delegate*.

### <a name="remarks"></a>Comentarios

Un evento es una asociación entre un delegado (delegate) y una función miembro (controlador de eventos) que responde a la activación del evento y permite a los clientes de cualquier clase registrar los métodos que cumplen con la firma y devuelven el tipo de delegado subyacente.

El delegado (delegate) puede tener uno o varios métodos asociados que se llamarán cuando su código indique que se ha producido el evento. Un evento de un programa puede estar disponible para otros programas diseñados para Common Language Runtime de .NET Framework .

Hay dos tipos de declaraciones de eventos:

*miembros de datos de eventos*<br/>
El compilador para eventos de miembro de datos crea el almacenamiento para el evento en forma de un miembro del tipo delegate.  Un miembro de datos de evento debe declararse dentro de una clase. Esto también se conoce como un evento trivial (vea el siguiente ejemplo de código).

*bloques de eventos*<br/>
Los bloques de eventos le permiten personalizar el comportamiento de los métodos add, remove y raise mediante su implementación. La firma de los métodos add, remove y raise debe coincidir con la firma del delegado (delegate).  Los eventos del bloque de eventos no son miembros de datos y cualquier uso como un miembro de datos generará un error del compilador.

El tipo de valor devuelto del controlador de eventos debe coincidir con el del delegado.

En .NET Framework, puede tratar un miembro de datos como si se tratara de un método en sí mismo (es decir, el método `Invoke` de su delegado correspondiente). Debe predefinir el tipo de delegado para declarar un miembro de datos de evento administrado. En cambio, un método de evento administrado define implícitamente el delegado administrado correspondiente si todavía no se ha definido.  Dispone de un ejemplo de código al final de este tema.

Al declarar un evento administrado, puede especificar que se agreguen y quiten los descriptores de acceso a los que se llamará cuando se agreguen o quiten los controladores de eventos mediante los operadores += y -=. Los métodos add, remove y raise pueden llamarse de forma explícita.

A continuación se indican los pasos para crear y utilizar eventos en Visual C++:

1. Cree o identifique a un delegado (delegate). Si va a definir su propio evento, también debe asegurarse de que hay un delegado para usar con la palabra clave **event**. Si el evento está predefinido, en .NET Framework, por ejemplo, entonces los consumidores del evento solo necesitan conocer el nombre del delegado.

2. Cree una clase que contenta:

   - Un evento creado desde el delegado (delegate).

   - (Opcional) Un método que compruebe que existe una instancia del delegado declarada con la palabra clave **event**. De lo contrario, esta lógica debe colocarse en el código que desencadena el evento.

   - Métodos que llaman al evento. Estos métodos pueden ser reemplazos de alguna funcionalidad de la clase base.

   Esta clase define el evento.

3. Defina una o más clases que conecte los métodos con el evento. Cada una de estas clases se asociará a uno o más métodos con el evento de la clase base.

4. Utilice el evento:

   - Cree un objeto de la clase que contenga la declaración del evento.

   - Cree un objeto de la clase que contenga la definición del evento.

Para más información sobre los eventos de C++/CLI, consulte el artículo sobre

- [los eventos en una interfaz](../dotnet/how-to-use-events-in-cpp-cli.md)

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

En el ejemplo de código siguiente se muestra la lógica usada para generar el método `raise` de un evento trivial: Si el evento tiene uno o varios suscriptores, al llamar al método `raise` de forma implícita o explícita se llamará al delegado. Si el tipo de valor devuelto del delegado no es **void** y si no hay ningún suscriptor de eventos, el método `raise` devolverá el valor predeterminado para el tipo delegado. Si no hay ningún suscriptor de eventos, llamar al método `raise` simplemente devuelve y no se genera ninguna excepción. Si el tipo de valor devuelto del delegado no es **void**, se devolverá el tipo delegado.

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

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)