---
title: "En la nube y Web de programación en Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-azure
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8c04939aea508afed60b32ae51d627a1f5d902fd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programación web y para la nube en Visual C++
En C++, existen varias opciones para conectarse a la Web y a la nube.  
  
 [Servicios móviles de Microsoft Azure](http://www.windowsazure.com/develop/mobile/)  
 Proporciona las API nativas que puede usar en las aplicaciones de la plataforma Universal de Windows (UWP) o aplicaciones de escritorio de Windows para conectarse a servicios móviles de Windows Azure. Aunque la mayoría de los ejemplos del sitio web están en C#, también se puede utilizar C++. Para obtener más información, vea [Inicio rápido: agregar un servicio móvil con C++](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx).  

 [Biblioteca de cliente de almacenamiento de Microsoft Azure para C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)  
 La biblioteca de cliente de almacenamiento de Azure para C++ proporciona una completa API para trabajar con el almacenamiento de Azure, incluyendo pero sin limitarse a las capacidades siguientes:

- Crear, leer, eliminar y enumerar los contenedores de blobs, tablas y colas.
- Crear, leer, eliminar, lista y copia blobs de más de lectura y escritura rangos de blob.
- INSERT, delete, replace, combinación y consultar entidades en una tabla de Azure.
- Enqueue y dequeue mensajes en una cola de Azure.
- Lista de forma diferida contenedores, blobs, tablas y colas y consultar las entidades de forma diferida

[API de OneDrive](https://dev.onedrive.com/README.htm)  
 La API de OneDrive proporciona un conjunto de servicios HTTP que se va a conectar su aplicación a archivos y carpetas en Office 365 y SharePoint Server 2016.

[SDK de REST de C++ (nombre código "Casablanca")](https://github.com/Microsoft/cpprestsdk)  
Proporciona una API moderna, multiplataforma y asincrónica para interactuar con los servicios REST.

-   Realizar llamadas REST en cualquier servidor HTTP, con la compatibilidad integrada para la serialización y análisis de documento JSON
-   Es compatible con OAuth 1 y 2, incluido un agente de escucha de redirección local
-   Establecer conexiones de Websockets con servicios remotos
-   Una tarea asincrónica totalmente API basada en PPL, incluyendo un subproceso threadpool integrado

Es compatible con el escritorio de Windows (7 +), Windows Server (2012 +), plataforma Universal de Windows, Linux, OSX, Android y iOS. 
  
[Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)  
 Una clase de cliente HTTP de Windows en tiempo de ejecución modelada en la clase .NET Framework del mismo nombre en el espacio de nombres System.Web. `HttpClient` es totalmente compatible con la carga y descarga asincrónica a través de HTTP y con los filtros de canalización que habilitan la inserción de controladores HTTP personalizados en la canalización. Windows SDK incluye filtros de ejemplo para redes de uso medido y autenticación de OAuth, entre otros. Para las aplicaciones que tienen como destino la plataforma Universal de Windows, se recomienda que realice la `Windows::Web:HttpClient` clase. 
  
[Interfaz IXMLHTTPRequest2](http://msdn.microsoft.com/library/windows/apps/hh831151.aspx)  
 Proporciona una interfaz COM nativa que puede utilizar en aplicaciones de Windows Runtime o aplicaciones de escritorio de Windows para conectarse a Internet a través de HTTP y emitir comandos GET, PUT y otros comandos HTTP. Para obtener más información, consulte [Tutorial: conectar usando tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).  
  
[Windows Internet (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)  
 API de Windows que se puede utilizar en aplicaciones de escritorio de Windows para conectarse a Internet.  
  
## <a name="see-also"></a>Vea también  
 [Visual C++](../visual-cpp-in-visual-studio.md)   
 [Redes y servicios web](/windows/uwp/networking/)