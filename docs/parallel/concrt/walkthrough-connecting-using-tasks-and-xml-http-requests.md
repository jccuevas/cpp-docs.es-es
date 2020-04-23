---
title: 'Tutorial: Conectar usando tareas y solicitudes HTTP XML'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: 2c627a543ec18702bf5358ff0170bec177fd7497
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032270"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Tutorial: Conectar usando tareas y solicitudes HTTP XML

En este ejemplo se muestra cómo usar las interfaces [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) e [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) junto con tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación para la Plataforma universal de Windows (UWP). Mediante la combinación de `IXMLHTTPRequest2` junto con las tareas, puede escribir código que se crea con otras tareas. Por ejemplo, puede usar la tarea de descarga como parte de una cadena de tareas. La tarea de descarga también puede responder cuando se cancela el trabajo.

> [!TIP]
> También puedes usar el SDK de REST de C++ para realizar solicitudes HTTP desde una aplicación para UWP mediante la aplicación C++ o desde una aplicación C++ de escritorio. Para obtener más información, consulte [C++ REST SDK (Nombre de código "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Para obtener más información acerca de las tareas, consulte [Paralelismo](../../parallel/concrt/task-parallelism-concurrency-runtime.md)de tareas . Para obtener más información sobre cómo usar tareas en una aplicación para UWP, consulta [Programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) y Creación de [operaciones asincrónicas en C++ para aplicaciones para UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

En este documento se muestra primero cómo crear `HttpRequest` y sus clases auxiliares. A continuación, muestra cómo usar esta clase desde una aplicación para UWP que usa C++ y XAML.

Para obtener un `IXMLHTTPRequest2` ejemplo que utiliza pero no utiliza tareas, consulte Inicio rápido: conexión mediante solicitud [HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
> `IXMLHTTPRequest2`y `IXMLHTTPRequest2Callback` son las interfaces que recomendamos para su uso en una aplicación para UWP. También puede adaptar este ejemplo para usarlo en una aplicación de escritorio.

## <a name="prerequisites"></a>Requisitos previos

La compatibilidad con UWP es opcional en Visual Studio 2017 y versiones posteriores. Para instalarlo, abra el instalador de Visual Studio desde el menú Inicio de Windows y elija la versión de Visual Studio que está utilizando. Haz clic en el botón **Modificar** y asegúrate de que el icono Desarrollo de **UWP** esté activado. En **Componentes opcionales,** asegúrate de que **C++ UWP Tools** esté activado. Use v141 para Visual Studio 2017 o v142 para Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definir las clases HttpRequest, HttpRequestBuffersCallback y HttpRequestStringCallback

Cuando se utiliza la interfaz `IXMLHTTPRequest2` para crear solicitudes web sobre HTTP, se implementa la interfaz `IXMLHTTPRequest2Callback` para recibir la respuesta del servidor y reaccionar a otros eventos. En este ejemplo se define la clase `HttpRequest` para crear solicitudes web y las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` para procesar las respuestas. Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` admiten la clase `HttpRequest`; trabaja solamente con la clase `HttpRequest` del código de la aplicación.

Los métodos `GetAsync`, `PostAsync` de la clase `HttpRequest` permiten iniciar las operaciones HTTP GET y POST, respectivamente. Estos métodos utilizan la clase `HttpRequestStringCallback` para leer la respuesta del servidor como una cadena. Los métodos `SendAsync` y `ReadAsync` permiten hacer streaming del contenido grande en fragmentos. Cada uno de estos métodos devuelve [concurrency::task](../../parallel/concrt/reference/task-class.md) para representar la operación. Los métodos `GetAsync` y `PostAsync` generan el valor `task<std::wstring>`, donde la parte `wstring` representa la respuesta del servidor. Los métodos `SendAsync` y de `ReadAsync` generan los valores `task<void>`; estas tareas se completan cuando las operaciones de envío y lectura se completan.

Dado `IXMLHTTPRequest2` que las interfaces actúan de forma asincrónica, en este ejemplo se usa [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) para crear una tarea que se completa después de que el objeto de devolución de llamada complete o cancele la operación de descarga. La clase `HttpRequest` crea una continuación basada en tareas a partir de esta tarea para establecer el resultado final. La clase `HttpRequest` utiliza una continuación basada en tareas para garantizar que la tarea de continuación se ejecuta aunque la tarea anterior produzca un error o se cancele. Para obtener más información acerca de las continuaciones basadas en tareas, consulte [Paralelismo](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de tareas

Para admitir la cancelación, las clases `HttpRequest`, `HttpRequestBuffersCallback` y `HttpRequestStringCallback` utilizan tokens de cancelación. Las `HttpRequestBuffersCallback` `HttpRequestStringCallback` clases y usan el método [concurrency:cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) para permitir que el evento de finalización de la tarea responda a la cancelación. Esta devolución de llamada de cancelación anula la descarga. Para obtener más información sobre la cancelación, consulta [Cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

### <a name="to-define-the-httprequest-class"></a>Para definir la clase HttpRequest

1. En el menú principal, elija **Archivo** > **nuevo** > **proyecto**.

1. Use la plantilla Aplicación en blanco de C++ **(Windows universal)** para crear un proyecto de aplicación XAML en blanco. En este ejemplo, se asigna al proyecto el nombre `UsingIXMLHTTPRequest2`.

1. Agregue al proyecto un archivo de encabezado que se denomina HttpRequest.h y un archivo de código fuente denominado HttpRequest.cpp.

1. En pch.h, agregue este código:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. En HttpRequest.h, agregue este código:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. En HttpRequest.cpp, agregue este código:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Uso de la clase HttpRequest en una aplicación para UWP

En esta sección se `HttpRequest` muestra cómo usar la clase en una aplicación para UWP. La aplicación proporciona un cuadro de entrada que define un recurso de dirección URL y los comandos de botón que realizan las operaciones GET y POST, así como un comando de botón que cancela la operación actual.

### <a name="to-use-the-httprequest-class"></a>Para usar la clase HttpRequest

1. En MainPage.xaml, defina el elemento [StackPanel](/uwp/api/windows.ui.xaml.controls.stackpanel) de la siguiente manera.

   [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]

1. En MainPage.xaml.h, agregue esta directiva `#include`:

   [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]

1. En MainPage.xaml.h, agregue a estas variables de miembro `private` a la clase `MainPage`:

   [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]

1. En MainPage.xaml.h, declare el método `private``ProcessHttpRequest`:

   [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]

1. En MainPage.xaml.cpp, agregue estas instrucciones `using`:

   [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]

1. En MainPage.xaml.cpp, implemente los métodos `GetButton_Click`, `PostButton_Click` y `CancelButton_Click` de la clase `MainPage`.

   [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]

   > [!TIP]
   > Si la aplicación no requiere compatibilidad con la cancelación, pase `HttpRequest::GetAsync` `HttpRequest::PostAsync` [concurrency::cancellation_token::none](reference/cancellation-token-class.md#none) a los métodos y.

1. En MainPage.xaml.cpp, implemente el método `MainPage::ProcessHttpRequest`.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. En las propiedades del proyecto, en `shcore.lib` `msxml6.lib` **Vinculador**, **Entrada**, especifique y .

Esta es la aplicación en ejecución:

![La aplicación de Windows runtime en ejecución en ejecución](../../parallel/concrt/media/concrt_usingixhr2.png "La aplicación de Windows runtime en ejecución en ejecución")

## <a name="next-steps"></a>Pasos siguientes

[Tutoriales en tiempo de ejecución de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Vea también

[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Programación asíncrona en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Creación de operaciones asincrónicas en C++ para aplicaciones para UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Inicio rápido: Conexión mediante](/previous-versions/windows/apps/hh770550\(v=win.10\))
la clase de tarea Solicitud HTTP XML (IXMLHTTPRequest2) (en tiempo de ejecución de[simultaneidad)](../../parallel/concrt/reference/task-class.md)<br/>
[Clase task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)
