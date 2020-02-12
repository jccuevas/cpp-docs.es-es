---
title: 'Tutorial: Conectar usando tareas y solicitudes HTTP XML'
ms.date: 04/25/2019
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
ms.openlocfilehash: f1d91e4d203e17242bcf6e784d1ef70a03a9bc33
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142059"
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Tutorial: Conectar usando tareas y solicitudes HTTP XML

En este ejemplo se muestra cómo usar las interfaces [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) e [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) junto con las tareas para enviar solicitudes HTTP GET y post a un servicio web en una aplicación plataforma universal de Windows (UWP). Mediante la combinación de `IXMLHTTPRequest2` junto con las tareas, puede escribir código que se crea con otras tareas. Por ejemplo, puede usar la tarea de descarga como parte de una cadena de tareas. La tarea de descarga también puede responder cuando se cancela el trabajo.

> [!TIP]
> También puede usar el C++ SDK de REST para realizar solicitudes HTTP desde una aplicación de UWP C++ con una aplicación o desde C++ una aplicación de escritorio. Para obtener más información, consulte [ C++ el tema sobre el SDK de REST (nombre de código "Casablanca")](https://github.com/Microsoft/cpprestsdk).

Para obtener más información sobre las tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información sobre cómo usar las tareas en una aplicación de UWP, consulte [programación asincrónica C++ en](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) y [creación de C++ operaciones asincrónicas en para aplicaciones para UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

En este documento se muestra primero cómo crear `HttpRequest` y sus clases auxiliares. A continuación, se muestra cómo usar esta clase desde una aplicación de UWP C++ que usa y XAML.

Para obtener un ejemplo que usa `IXMLHTTPRequest2` pero no usa tareas, consulte [Inicio rápido: conectarse mediante una solicitud HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\)).

> [!TIP]
> `IXMLHTTPRequest2` y `IXMLHTTPRequest2Callback` son las interfaces que se recomienda usar en una aplicación de UWP. También puede adaptar este ejemplo para usarlo en una aplicación de escritorio.

## <a name="prerequisites"></a>Prerequisites

La compatibilidad con UWP es opcional en Visual Studio 2017 y versiones posteriores. Para instalarlo, abra el Instalador de Visual Studio desde el menú Inicio de Windows y elija la versión de Visual Studio que está usando. Haga clic en el botón **modificar** y asegúrese de que está seleccionado el icono **desarrollo de UWP** . En **componentes opcionales** , asegúrese de **C++** que esté activada la opción herramientas de UWP. Use v141 para Visual Studio 2017 o v142 para Visual Studio 2019.

## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definir las clases HttpRequest, HttpRequestBuffersCallback y HttpRequestStringCallback

Cuando se utiliza la interfaz `IXMLHTTPRequest2` para crear solicitudes web sobre HTTP, se implementa la interfaz `IXMLHTTPRequest2Callback` para recibir la respuesta del servidor y reaccionar a otros eventos. En este ejemplo se define la clase `HttpRequest` para crear solicitudes web y las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` para procesar las respuestas. Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` admiten la clase `HttpRequest`; trabaja solamente con la clase `HttpRequest` del código de la aplicación.

Los métodos `GetAsync`, `PostAsync` de la clase `HttpRequest` permiten iniciar las operaciones HTTP GET y POST, respectivamente. Estos métodos utilizan la clase `HttpRequestStringCallback` para leer la respuesta del servidor como una cadena. Los métodos `SendAsync` y `ReadAsync` permiten hacer streaming del contenido grande en fragmentos. Estos métodos devuelven [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) para representar la operación. Los métodos `GetAsync` y `PostAsync` generan el valor `task<std::wstring>`, donde la parte `wstring` representa la respuesta del servidor. Los métodos `SendAsync` y de `ReadAsync` generan los valores `task<void>`; estas tareas se completan cuando las operaciones de envío y lectura se completan.

Dado que las interfaces de `IXMLHTTPRequest2` actúan de forma asincrónica, en este ejemplo se usa [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) para crear una tarea que se completa después de que el objeto de devolución de llamada finalice o cancele la operación de descarga. La clase `HttpRequest` crea una continuación basada en tareas a partir de esta tarea para establecer el resultado final. La clase `HttpRequest` utiliza una continuación basada en tareas para garantizar que la tarea de continuación se ejecuta aunque la tarea anterior produzca un error o se cancele. Para obtener más información acerca de las continuaciones basadas en tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) .

Para admitir la cancelación, las clases `HttpRequest`, `HttpRequestBuffersCallback` y `HttpRequestStringCallback` utilizan tokens de cancelación. Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` usan el método [Concurrency:: cancellation_token:: register_callback](reference/cancellation-token-class.md#register_callback) para permitir que el evento de finalización de la tarea responda a la cancelación. Esta devolución de llamada de cancelación anula la descarga. Para obtener más información sobre la cancelación, vea [cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

### <a name="to-define-the-httprequest-class"></a>Para definir la clase HttpRequest

1. En el menú principal, elija **archivo** > **nuevo** **proyecto**de > .

1. Use la C++ plantilla **aplicación vacía (Windows universal)** para crear un proyecto de aplicación XAML en blanco. En este ejemplo, se asigna al proyecto el nombre `UsingIXMLHTTPRequest2`.

1. Agregue al proyecto un archivo de encabezado que se denomina HttpRequest.h y un archivo de código fuente denominado HttpRequest.cpp.

1. En pch.h, agregue este código:

   [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]

1. En HttpRequest.h, agregue este código:

   [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]

1. En HttpRequest.cpp, agregue este código:

   [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]

## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Usar la clase HttpRequest en una aplicación de UWP

En esta sección se muestra cómo usar la clase `HttpRequest` en una aplicación de UWP. La aplicación proporciona un cuadro de entrada que define un recurso de dirección URL y los comandos de botón que realizan las operaciones GET y POST, así como un comando de botón que cancela la operación actual.

### <a name="to-use-the-httprequest-class"></a>Para usar la clase HttpRequest

1. En MainPage. XAML, defina el elemento [StackPanel](/uwp/api/Windows.UI.Xaml.Controls.StackPanel) como se indica a continuación.

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
   > Si la aplicación no requiere compatibilidad para la cancelación, pase [Concurrency:: cancellation_token:: None](reference/cancellation-token-class.md#none) a los métodos `HttpRequest::GetAsync` y `HttpRequest::PostAsync`.

1. En MainPage.xaml.cpp, implemente el método `MainPage::ProcessHttpRequest`.

   [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]

1. En las propiedades del proyecto, en **vinculador**, **entrada**, especifique `shcore.lib` y `msxml6.lib`.

Esta es la aplicación en ejecución:

![La aplicación Windows Runtime en ejecución](../../parallel/concrt/media/concrt_usingixhr2.png "La aplicación Windows Runtime en ejecución")

## <a name="next-steps"></a>Pasos siguientes

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)

## <a name="see-also"></a>Consulte también

[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Programación asincrónica enC++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)<br/>
[Creación de operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)<br/>
[Inicio rápido: conexión mediante la solicitud HTTP XML (IXMLHTTPRequest2)](/previous-versions/windows/apps/hh770550\(v=win.10\))
[clase de tarea (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)<br/>
[task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)
