---
title: "Tutorial: Conectar usando tareas y solicitudes HTTP XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conectarse a servicios web, aplicaciones de Tienda Windows [C++]"
  - "IXMLHTTPRequest2 y tareas, ejemplo"
  - "IXHR2 y tareas, ejemplo"
ms.assetid: e8e12d46-604c-42a7-abfd-b1d1bb2ed6b3
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Conectar usando tareas y solicitudes HTTP XML
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo utilizar las interfaces [IXMLHTTPRequest2](http://msdn.microsoft.com/es-es/bbc11c4a-aecf-4d6d-8275-3e852e309908) e [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/es-es/aa4b3f4c-6e28-458b-be25-6cce8865fc71) junto con otras tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de la [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Mediante la combinación de `IXMLHTTPRequest2` junto con las tareas, puede escribir código que se crea con otras tareas.  Por ejemplo, puede usar la tarea de descarga como parte de una cadena de tareas.  La tarea de descarga también puede responder cuando se cancela el trabajo.  
  
> [!TIP]
>  Además, puede utilizar SDK de REST de C\+\+ para realizar solicitudes HTTP desde una aplicación [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] mediante una aplicación C\+\+ o desde una aplicación de escritorio C\+\+.  Para obtener más información, vea [SDK de REST de C\+\+ \(nombre código "Casablanca"\)](../../top/cpp-rest-sdk-codename-casablanca.md).  
  
 Para obtener más información acerca de las tareas, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  Para obtener más información sobre cómo usar tareas en una aplicación [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], vea [Asynchronous programming in C\+\+](http://msdn.microsoft.com/es-es/512700b7-7863-44cc-93a2-366938052f31) y [Crear operaciones asincrónicas en C\+\+ para aplicaciones de la Tienda Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).  
  
 En este documento se muestra primero cómo crear `HttpRequest` y sus clases auxiliares.  A continuación se muestra cómo utilizar esta clase desde una aplicación [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] que usa C\+\+ y XAML.  
  
 Para obtener un ejemplo más completo que utiliza la clase `HttpReader` descrita en este documento, vea [Desarrollar el optimizador de recorridos de Mapas de Bing, una aplicación de la Tienda Windows en JavaScript y C\+\+](../Topic/Developing%20Bing%20Maps%20Trip%20Optimizer,%20a%20Windows%20Store%20app%20in%20JavaScript%20and%20C++.md).  Para obtener otro ejemplo que utiliza `IXMLHTTPRequest2` pero no usa tareas, vea [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/es-es/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35).  
  
> [!TIP]
>  `IXMLHTTPRequest2` y `IXMLHTTPRequest2Callback` son las interfaces que se recomiendan para usarlas en una aplicación [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  También puede adaptar este ejemplo para usarlo en una aplicación de escritorio.  
  
## Requisitos previos  
  
## Definir las clases HttpRequest, HttpRequestBuffersCallback y HttpRequestStringCallback  
 Cuando se utiliza la interfaz `IXMLHTTPRequest2` para crear solicitudes web sobre HTTP, se implementa la interfaz `IXMLHTTPRequest2Callback` para recibir la respuesta del servidor y reaccionar a otros eventos.  En este ejemplo se define la clase `HttpRequest` para crear solicitudes web y las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` para procesar las respuestas.  Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` admiten la clase `HttpRequest`; trabaja solamente con la clase `HttpRequest` del código de la aplicación.  
  
 Los métodos `GetAsync`, `PostAsync` de la clase `HttpRequest` permiten iniciar las operaciones HTTP GET y POST, respectivamente.  Estos métodos utilizan la clase `HttpRequestStringCallback` para leer la respuesta del servidor como una cadena.  Los métodos `SendAsync` y `ReadAsync` permiten hacer streaming del contenido grande en fragmentos.  Cada uno de estos métodos devuelve [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) para representar la operación.  Los métodos `GetAsync` y `PostAsync` generan el valor `task<std::wstring>`, donde la parte `wstring` representa la respuesta del servidor.  Los métodos `SendAsync` y de `ReadAsync` generan los valores `task<void>`; estas tareas se completan cuando las operaciones de envío y lectura se completan.  
  
 Dado que las interfaces de `IXMLHTTPRequest2` actúan de forma asincrónica, en este ejemplo se utiliza [concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md) para crear una tarea que finaliza después de que el objeto de devolución de llamada completa o cancela la operación de descarga.  La clase `HttpRequest` crea una continuación basada en tareas a partir de esta tarea para establecer el resultado final.  La clase `HttpRequest` utiliza una continuación basada en tareas para garantizar que la tarea de continuación se ejecuta aunque la tarea anterior produzca un error o se cancele.  Para obtener más información sobre continuaciones basadas en tareas, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Para admitir la cancelación, las clases `HttpRequest`, `HttpRequestBuffersCallback` y `HttpRequestStringCallback` utilizan tokens de cancelación.  Las clases `HttpRequestBuffersCallback` y `HttpRequestStringCallback` utilizan el método [concurrency::cancellation\_token::register\_callback](../Topic/cancellation_token::register_callback%20Method.md) para habilitar el evento de finalización de la tarea y responder a la cancelación.  Esta devolución de llamada de cancelación anula la descarga.  Para obtener más información sobre la cancelación, vea [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
#### Para definir la clase HttpRequest  
  
1.  Utilice la plantilla de Visual C\+\+ **Aplicación vacía \(XAML\)** para crear un proyecto de aplicación de archivo XAML en blanco.  En este ejemplo se asigna el nombre al proyecto `UsingIXMLHTTPRequest2`.  
  
2.  Agregue al proyecto un archivo de encabezado que se denomina HttpRequest.h y un archivo de código fuente denominado HttpRequest.cpp.  
  
3.  En pch.h, agregue este código:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#1](concrt-using-IXMLHTTPRequest2#1)]  
  
4.  En HttpRequest.h, agregue este código:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#2](concrt-using-IXMLHTTPRequest2#2)]  
  
5.  En HttpRequest.cpp, agregue este código:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#3](concrt-using-IXMLHTTPRequest2#3)]  
  
## Usar la clase HttpRequest en una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]  
 En esta sección se muestra cómo utilizar la clase `HttpRequest` en una aplicación [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  La aplicación proporciona un cuadro de entrada que define un recurso de dirección URL y los comandos de botón que realizan las operaciones GET y POST, así como un comando de botón que cancela la operación actual.  
  
#### Para usar la clase HttpRequest  
  
1.  En MainPage.xaml, defina el elemento [StackPanel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.stackpanel.aspx) como sigue.  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A1](concrt-using-IXMLHTTPRequest2#A1)]  
  
2.  En MainPage.xaml.h, agregue esta directiva `#include`:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A2](concrt-using-IXMLHTTPRequest2#A2)]  
  
3.  En MainPage.xaml.h, agregue a estas variables de miembro `private` a la clase `MainPage`:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A3](concrt-using-IXMLHTTPRequest2#A3)]  
  
4.  En MainPage.xaml.h, declare el método `ProcessHttpRequest` `private`:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A4](concrt-using-IXMLHTTPRequest2#A4)]  
  
5.  En MainPage.xaml.cpp, agregue estas instrucciones `using`:  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A5](concrt-using-IXMLHTTPRequest2#A5)]  
  
6.  En MainPage.xaml.cpp, implemente los métodos `GetButton_Click`, `PostButton_Click` y `CancelButton_Click` de la clase `MainPage`.  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A6](concrt-using-IXMLHTTPRequest2#A6)]  
  
    > [!TIP]
    >  Si la aplicación no requiere la admisión de la cancelación, pase [concurrency::cancellation\_token::none](../Topic/cancellation_token::none%20Method.md) a los métodos `HttpRequest::GetAsync` y `HttpRequest::PostAsync`.  
  
7.  En MainPage.xaml.cpp, implemente el método `MainPage::ProcessHttpRequest`.  
  
     [!CODE [concrt-using-IXMLHTTPRequest2#A7](concrt-using-IXMLHTTPRequest2#A7)]  
  
8.  En las propiedades del proyecto, en **Vinculador**, **Entrada**, especifique `shcore.lib` y `msxml6.lib`.  
  
 Esta es la aplicación en ejecución:  
  
 ![Aplicación de la Tienda Windows en ejecución](../../parallel/concrt/media/concrt_usingixhr2.png "ConcRT\_UsingIXHR2")  
  
## Pasos siguientes  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)  
  
## Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Asynchronous programming in C\+\+](http://msdn.microsoft.com/es-es/512700b7-7863-44cc-93a2-366938052f31)   
 [Crear operaciones asincrónicas en C\+\+ para aplicaciones de la Tienda Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)   
 [Quickstart: Connecting using XML HTTP Request \(IXMLHTTPRequest2\)](http://msdn.microsoft.com/es-es/cc7aed53-b2c5-4d83-b85d-cff2f5ba7b35)   
 [task \(Clase\) \(Motor en tiempo de ejecución de simultaneidad\)](../../parallel/concrt/reference/task-class-concurrency-runtime.md)   
 [task\_completion\_event \(Clase\)](../../parallel/concrt/reference/task-completion-event-class.md)   
 [IXMLHTTPRequest2](http://msdn.microsoft.com/es-es/bbc11c4a-aecf-4d6d-8275-3e852e309908)   
 [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/es-es/aa4b3f4c-6e28-458b-be25-6cce8865fc71)