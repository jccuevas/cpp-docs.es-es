---
title: Delegados (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42ca9673efe45ca816208e87ef0f0153d069e4a9
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108432"
---
# <a name="delegates-ccx"></a>Delegados (C++/CX)

El `delegate` palabra clave se usa para declarar un tipo de referencia que es el equivalente de Windows en tiempo de ejecución de un objeto de función en C++ estándar. Una declaración de delegado es similar a una signatura de función; especifica el tipo de valor devuelto y los tipos de parámetros que debe tener la función incluida. Esta es una declaración de delegado definida por el usuario:

```cpp
public delegate void PrimeFoundHandler(int result);
```

Los delegados suelen usarse junto con eventos. Un evento tiene un tipo de delegado, de la misma manera que una clase puede tener un tipo de interfaz. El delegado representa un contrato que deben cumplir los controladores de eventos. A continuación se muestra un miembro de la clase de evento cuyo tipo es el delegado definido previamente:

```cpp
event PrimeFoundHandler^ primeFoundEvent;
```

Al declarar los delegados que se expondrán a los clientes a través de la interfaz binaria de aplicación de Windows en tiempo de ejecución, utilice [Windows::Foundation::TypedEventHandler\<TSender, TResult >](https://msdn.microsoft.com/library/windows/apps/br225997.aspx). Este delegado tiene binarios de código auxiliar y proxy predefinidos que permiten su uso en clientes de JavaScript.

## <a name="consuming-delegates"></a>Usar delegados

Cuando se crea una aplicación plataforma Universal de Windows, sueles trabajar con un delegado como el tipo de un evento que expone una clase en tiempo de ejecución de Windows. Para suscribirte a un evento, crea una instancia de su tipo de delegado especificando una función, o expresión lambda, que coincida con la firma de delegado. Después, usa el operador `+=` para pasar el objeto de delegado al miembro de evento de la clase. Esto se denomina suscribirse al evento. Cuando la instancia de clase "desencadena" el evento, se llama a tu función junto con cualquier otro controlador que haya sido agregado por tu objeto o por otros objetos.

> [!TIP]
> Visual Studio realiza mucho trabajo automáticamente cuando creas un controlador de eventos. Por ejemplo, si especificas un controlador de eventos en marcado XAML, aparece una información sobre herramientas. Si eliges la información sobre herramientas, Visual Studio crea automáticamente el método de controlador de eventos y lo asocia al evento en la clase de publicación.

En el ejemplo siguiente se muestra el patrón básico. `Windows::Foundation::TypedEventHandler` es el tipo de delegado. La función de controlador se crea utilizando una función con nombre.

En app.h:

[!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]

En app.cpp:

[!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]

> [!WARNING]
> En general, para un controlador de eventos es mejor usar una función con nombre en lugar de una expresión lambda, a menos que tengas mucho cuidado para evitar referencias circulares. Una función con nombre captura el puntero "this" mediante referencia débil, mientras que una expresión lambda lo captura mediante referencia segura y crea una referencia circular. Para obtener más información, consulte [referencias débiles e interrupción de ciclos](../cppcx/weak-references-and-breaking-cycles-c-cx.md).

Por convención, los nombres de delegado de controlador de eventos definidos por el tiempo de ejecución de Windows tienen el formato * EventHandler; por ejemplo, RoutedEventHandler, SizeChangedEventHandler o SuspendingEventHandler. También por convención, los delegados de controladores de eventos tienen dos parámetros y devuelven void. En un delegado que no tiene parámetros de tipo, el primer parámetro es de tipo [Platform::Object^](../cppcx/platform-object-class.md); contiene una referencia al remitente, que es el objeto que desencadenó el evento. Tienes que volver a convertir al tipo original antes de usar el argumento en el método de controlador de eventos. En un delegado de controlador de eventos que tiene parámetros de tipo, el primer parámetro de tipo especifica el tipo del remitente y el segundo parámetro es un identificador de una clase ref que contiene información sobre el evento. Por convención, la clase se denomina \*EventArgs. Por ejemplo, un delegado RoutedEventHandler tiene un segundo parámetro de tipo RoutedEventArgs^ y DragEventHander tiene un segundo parámetro de tipo DragEventArgs^.

Por convención, los delegados que contienen el código que se ejecuta cuando se completa una operación asincrónica se denominan *CompletedHandler. Estos delegados se definen como propiedades en la clase, no como eventos. Por consiguiente, no se utiliza el operador `+=` para suscribirse a ellas; solo tienes que asignar un objeto de delegado a la propiedad.

> [!TIP]
> IntelliSense de C++ no muestra la firma completa de delegado; por tanto, no ayuda a determinar el tipo específico del parámetro EventArgs. Para encontrar el tipo, puedes ir al **Examinador de objetos** y ver el método `Invoke` para el delegado.

## <a name="creating-custom-delegates"></a>Crear delegados personalizados

Puede definir sus propios delegados para definir controladores de eventos o para permitir que los consumidores pasen funcionalidad personalizada a su componente en tiempo de ejecución de Windows. Como cualquier otro tipo en tiempo de ejecución de Windows, un delegado público no se puede declarar como genérico.

### <a name="declaration"></a>Declaración

La declaración de un delegado es similar a una declaración de función salvo que el delegado es un tipo. Normalmente, declaras un delegado en el ámbito del espacio de nombres, aunque también puedes anidar una declaración de delegado en una declaración de clase. El delegado siguiente encapsula cualquier función que toma `ContactInfo^` como entrada y devuelve `Platform::String^`.

[!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]

Después de declarar un tipo de delegado, puedes declarar miembros de clase de ese tipo o métodos que toman objetos de ese tipo como parámetros. Un método o una función también puede devolver un tipo de delegado. En el ejemplo siguiente, el método `ToCustomString` toma el delegado como parámetro de entrada. El método permite que el código de cliente proporcione una función personalizada que construye una cadena a partir de algunas o de todas las propiedades públicas de un objeto `ContactInfo` .

[!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]

> [!NOTE]
> Usa el "^" símbolos cuando se hace referencia al tipo de delegado, igual que con cualquier tiempo de ejecución de Windows tipo de referencia.

Una declaración de evento siempre tiene un tipo de delegado. Este ejemplo muestra un delegado habitual signatura de tipo en tiempo de ejecución de Windows:

[!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]

El evento `Click` de la clase `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` es de tipo `RoutedEventHandler`. Para obtener más información, consulta [Events](../cppcx/events-c-cx.md).

El código de cliente primero crea la instancia del delegado mediante `ref new` y proporcionando una expresión lambda que es compatible con la firma de delegado y define el comportamiento personalizado.

[!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]

Después llama a la función miembro y pasa el delegado. Imagina que `ci` es una instancia de `ContactInfo^` y `textBlock` es un `TextBlock^`XAML.

[!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]

En el ejemplo siguiente, una aplicación cliente pasa un delegado personalizado a un método público de un componente de tiempo de ejecución de Windows que ejecuta el delegado en cada elemento en un `Vector`:

[!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]

[!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]

### <a name="construction"></a>Construcción

Puedes construir un delegado a partir de cualquiera de estos objetos:

- lambda

- función estática

- puntero a miembro

- std::function

En el ejemplo siguiente se muestra cómo construir un delegado a partir de cada uno de estos objetos. Usa el delegado de la misma forma independientemente del tipo de objeto que se use para crearlo.

[!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]

> [!WARNING]
> Si empleas una expresión lambda que captura el puntero “this”, asegúrate de usar el operador `-=` para anular explícitamente el registro del evento antes de salir de la expresión lambda. Para más información, vea [Eventos](../cppcx/events-c-cx.md).

### <a name="generic-delegates"></a>Delegados genéricos

Los delegados genéricos en C++/CX tienen restricciones similares a las declaraciones de clases genéricas. No pueden declararse como públicos. Puedes declarar un delegado genérico interno o privado y utilizarlo desde C++, pero los clientes de .NET o JavaScript no podrán usarlo porque no se emite en los metadatos .winmd. En este ejemplo se declara un delegado genérico que solo se puede utilizar en C++:

[!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]

En el ejemplo siguiente se declara una instancia especializada del delegado dentro de una definición de clase:

[!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]

## <a name="delegates-and-threads"></a>Delegados y subprocesos

Un delegado, como un objeto de función, contiene código que se ejecutará en algún momento en el futuro. Si el código que crea y pasa el delegado, y la función que acepta y ejecuta el delegado, se están ejecutando en el mismo subproceso, las cosas son relativamente simples. Si ese subproceso es el subproceso de la interfaz de usuario, el delegado puede manipular directamente objetos de la interfaz de usuario como controles XAML.

A continuación, si una aplicación cliente carga un componente en tiempo de ejecución de Windows que se ejecuta en un contenedor uniproceso y proporciona a un delegado a ese componente, de forma predeterminada el delegado se invoca directamente en el subproceso STA. Puede ejecutar la mayoría de los componentes de Windows en tiempo de ejecución en STA o MTA.

Si el código que ejecuta el delegado se está ejecutando en otro subproceso (por ejemplo, en el contexto de un objeto concurrency::task), tú eres responsable de sincronizar el acceso a los datos compartidos. Por ejemplo, si tu delegado contiene una referencia a un Vector y un control XAML tiene una referencia a ese mismo Vector, debes realizar los pasos necesarios para evitar interbloqueos o condiciones de carrera que pueden producirse cuando tanto el delegado como el control XAML intentan obtener acceso al Vector al mismo tiempo. También debes tener cuidado para que el delegado no intente capturar por referencia las variables locales que podrían salir del ámbito antes de que se invoque el delegado.

Si deseas que se vuelva a llamar al delegado que has creado en el mismo subproceso en el que lo creaste (por ejemplo, si lo pasas a un componente que se ejecuta en un contenedor MTA) y deseas que se invoque en el mismo subproceso que el creador, usa la sobrecarga del constructor delegado que toma un segundo parámetro `CallbackContext` . Usa solo esta sobrecarga en delegados que tengan un proxy o código auxiliar registrado; no todos los delegados que se definen en Windows.winmd están registrados.

Si estás familiarizado con los controladores de eventos de .NET, ya sabrás que la práctica recomendada consiste en crear una copia local de un evento antes de desencadenarlo. Esto evita las condiciones de carrera en las que se podría quitar un controlador de eventos justo antes de invocar al evento. No es necesario hacer esto en C++/CX, ya que cuando se agregan o quitan controladores de eventos se crea una nueva lista de controladores. Dado que un objeto C++ incrementa el recuento de referencias en la lista de controladores antes de invocar un evento, se garantiza que todos los controladores serán válidos. Sin embargo, esto también significa que si quitas un controlador de eventos en el subproceso utilizado, se podría seguir invocando a ese controlador si el objeto de publicación sigue funcionando en su copia de la lista, que ahora está obsoleta. El objeto de publicación no obtendrá la lista actualizada hasta la próxima vez que desencadene el evento.

## <a name="see-also"></a>Vea también

[Sistema de tipos](../cppcx/type-system-c-cx.md)<br/>
[Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)