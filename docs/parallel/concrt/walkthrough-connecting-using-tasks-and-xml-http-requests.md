---
title: 'Tutorial: Conectar usando tareas y solicitudes HTTP XML | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- connecting to web services, UWP apps [C++]
- IXMLHTTPRequest2 and tasks, example
- IXHR2 and tasks, example
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 411d52201aad69a94267615cd0a2acbe6376f64d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="walkthrough-connecting-using-tasks-and-xml-http-requests"></a>Tutorial: Conectar usando tareas y solicitudes HTTP XML
Este ejemplo muestra cómo utilizar el [IXMLHTTPRequest2](http://msdn.microsoft.com/en-us/bbc11c4a-aecf-4d6d-8275-3e852e309908) y [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/en-us/aa4b3f4c-6e28-458b-be25-6cce8865fc71) interfaces junto con otras tareas para enviar solicitudes HTTP GET y POST a un servicio web en un Universal plataforma de Windows (UWP ) aplicación. Mediante la combinación de `IXMLHTTPRequest2` junto con las tareas, puede escribir código que se crea con otras tareas. Por ejemplo, puede usar la tarea de descarga como parte de una cadena de tareas. La tarea de descarga también puede responder cuando se cancela el trabajo.  
  
> [!TIP]
>  También puede usar el SDK de REST de C++ para realizar solicitudes HTTP desde una aplicación UWP con la aplicación de C++ o desde una aplicación de C++ de escritorio. Para obtener más información, consulte [C++ REST SDK (nombre de código "Casablanca")](https://github.com/Microsoft/cpprestsdk).  
  
 Para obtener más información acerca de las tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información acerca de cómo usar las tareas en una aplicación UWP, vea [programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) y [crear operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 En este documento se muestra primero cómo crear `HttpRequest` y sus clases auxiliares. A continuación, se muestra cómo utilizar esta clase desde una aplicación para UWP que usa C++ y XAML.  
  
 Para obtener un ejemplo más completo que usa el `HttpReader` clase descritas en este documento, consulte [desarrollar Bing Maps Trip Optimizer, una aplicación de tienda Windows en JavaScript y C++](http://msdn.microsoft.com/library/974cf025-de1a-4299-b7dd-c6c7bf0e5d30). Para obtener otro ejemplo que usa `IXMLHTTPRequest2` pero no usa tareas, consulte [inicio rápido: conectarse usando la solicitud de HTTP XML (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2` y `IXMLHTTPRequest2Callback` son las interfaces que se recomiendan para su uso en una aplicación de UWP. También puede adaptar este ejemplo para usarlo en una aplicación de escritorio.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
## <a name="defining-the-httprequest-httprequestbufferscallback-and-httprequeststringcallback-classes"></a>Definir las clases HttpRequest, HttpRequestBuffersCallback y HttpRequestStringCallback  
 Cuando se utiliza la interfaz `IXMLHTTPRequest2` para crear solicitudes web sobre HTTP, se implementa la interfaz `IXMLHTTPRequest2Callback` para recibir la respuesta del servidor y reaccionar a otros eventos. En este ejemplo se define la clase `HttpRequest` para crear solicitudes web y las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` para procesar las respuestas. Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` admiten la clase `HttpRequest`; trabaja solamente con la clase `HttpRequest` del código de la aplicación.  
  
 Los métodos `GetAsync`, `PostAsync` de la clase `HttpRequest` permiten iniciar las operaciones HTTP GET y POST, respectivamente. Estos métodos utilizan la clase `HttpRequestStringCallback` para leer la respuesta del servidor como una cadena. Los métodos `SendAsync` y `ReadAsync` permiten hacer streaming del contenido grande en fragmentos. Cada uno de estos métodos devuelve [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) para representar la operación. Los métodos `GetAsync` y `PostAsync` generan el valor `task<std::wstring>`, donde la parte `wstring` representa la respuesta del servidor. Los métodos `SendAsync` y de `ReadAsync` generan los valores `task<void>`; estas tareas se completan cuando las operaciones de envío y lectura se completan.  
  
 Dado que la `IXMLHTTPRequest2` interfaces actúan de forma asincrónica, este ejemplo se utiliza [task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) para crear una tarea que finaliza después el objeto de devolución de llamada completa o cancela la operación de descarga. La clase `HttpRequest` crea una continuación basada en tareas a partir de esta tarea para establecer el resultado final. La clase `HttpRequest` utiliza una continuación basada en tareas para garantizar que la tarea de continuación se ejecuta aunque la tarea anterior produzca un error o se cancele. Para obtener más información acerca de las continuaciones basadas en tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
 Para admitir la cancelación, las clases `HttpRequest`, `HttpRequestBuffersCallback` y `HttpRequestStringCallback` utilizan tokens de cancelación. El `HttpRequestBuffersCallback` y `HttpRequestStringCallback` clases utilizan el [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) método para habilitar el evento de finalización de tarea responder a la cancelación. Esta devolución de llamada de cancelación anula la descarga. Para obtener más información sobre la cancelación, consulte [cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
#### <a name="to-define-the-httprequest-class"></a>Para definir la clase HttpRequest  
  
1.  Usar Visual C++ **aplicación vacía (XAML)** plantilla para crear un proyecto de aplicación XAML en blanco. En este ejemplo, se asigna al proyecto el nombre `UsingIXMLHTTPRequest2`.  
  
2.  Agregue al proyecto un archivo de encabezado que se denomina HttpRequest.h y un archivo de código fuente denominado HttpRequest.cpp.  
  
3.  En pch.h, agregue este código:  
  
     [!code-cpp[concrt-using-ixhr2#1](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_1.h)]  
  
4.  En HttpRequest.h, agregue este código:  
  
     [!code-cpp[concrt-using-ixhr2#2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_2.h)]  
  
5.  En HttpRequest.cpp, agregue este código:  
  
     [!code-cpp[concrt-using-ixhr2#3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_3.cpp)]  
  
## <a name="using-the-httprequest-class-in-a-uwp-app"></a>Utilizar la clase HttpRequest en una aplicación de UWP  
 Esta sección muestra cómo utilizar la `HttpRequest` clase en una aplicación de UWP. La aplicación proporciona un cuadro de entrada que define un recurso de dirección URL y los comandos de botón que realizan las operaciones GET y POST, así como un comando de botón que cancela la operación actual.  
  
#### <a name="to-use-the-httprequest-class"></a>Para usar la clase HttpRequest  
  
1.  En MainPage.xaml, definir la [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) elemento como se indica a continuación.  
  
     [!code-xml[concrt-using-ixhr2#A1](../../parallel/concrt/codesnippet/xaml/walkthrough-connecting-using-tasks-and-xml-http-requests_4.xaml)]  
  
2.  En MainPage.xaml.h, agregue esta directiva `#include`:  
  
     [!code-cpp[concrt-using-ixhr2#A2](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_5.h)]  
  
3.  En MainPage.xaml.h, agregue a estas variables de miembro `private` a la clase `MainPage`:  
  
     [!code-cpp[concrt-using-ixhr2#A3](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_6.h)]  
  
4.  En MainPage.xaml.h, declare el método `private` `ProcessHttpRequest`:  
  
     [!code-cpp[concrt-using-ixhr2#A4](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_7.h)]  
  
5.  En MainPage.xaml.cpp, agregue estas instrucciones `using`:  
  
     [!code-cpp[concrt-using-ixhr2#A5](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_8.cpp)]  
  
6.  En MainPage.xaml.cpp, implemente los métodos `GetButton_Click`, `PostButton_Click` y `CancelButton_Click` de la clase `MainPage`.  
  
     [!code-cpp[concrt-using-ixhr2#A6](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_9.cpp)]  
  
    > [!TIP]


    >  Si la aplicación no necesita compatibilidad con la cancelación, pase [cancellation_token:: none](reference/cancellation-token-class.md#none) a la `HttpRequest::GetAsync` y `HttpRequest::PostAsync` métodos.  


  
7.  En MainPage.xaml.cpp, implemente el método `MainPage::ProcessHttpRequest`.  
  
     [!code-cpp[concrt-using-ixhr2#A7](../../parallel/concrt/codesnippet/cpp/walkthrough-connecting-using-tasks-and-xml-http-requests_10.cpp)]  
  
8.  En las propiedades del proyecto, en **vinculador**, **entrada**, especifique `shcore.lib` y `msxml6.lib`.  
  
 Esta es la aplicación en ejecución:  
  
 ![La aplicación en ejecución en tiempo de ejecución de Windows](../../parallel/concrt/media/concrt_usingixhr2.png "concrt_usingixhr2")  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## <a name="see-also"></a>Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)   
 [Programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps)   
 [Crear operaciones asincrónicas en C++ para aplicaciones UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Inicio rápido: Conectarse usando la solicitud de HTTP XML (IXMLHTTPRequest2)](http://msdn.microsoft.com/en-us/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [tarea (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)   
 [task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)
