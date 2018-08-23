---
title: En la nube y Web de programación en Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-azure
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 162abbae937e6eeae62dd9dfcd924af44dfd7270
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610045"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programación web y para la nube en Visual C++

En C++, existen varias opciones para conectarse a la Web y a la nube.

## <a name="cloud-programming-options"></a>Opciones de programación de nube

- [Servicios móviles de Microsoft Azure](http://www.windowsazure.com/develop/mobile/)

   Proporciona las API nativas que puede usar en aplicaciones de plataforma Universal de Windows (UWP) o aplicaciones de escritorio de Windows para conectarse a Microsoft Azure Mobile Services. Aunque la mayoría de los ejemplos del sitio web están en C#, también se puede utilizar C++. Para obtener más información, vea [Inicio rápido: agregar un servicio móvil con C++](http://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Biblioteca de cliente de Microsoft Azure Storage para C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

   La biblioteca de cliente de Azure Storage para C++ proporciona una API completa para trabajar con almacenamiento de Azure, incluyendo pero sin limitarse a las capacidades siguientes:

  - Crear, leer, eliminar y enumerar los contenedores de blobs, tablas y colas.
  - Crear, leer, eliminar, lista y copie blobs más leer y escribir intervalos del blob.
  - INSERT, delete, replace, combinación y consultar entidades en una tabla de Azure.
  - Poner en cola y eliminación de cola de mensajes en una cola de Azure.
  - Lista de forma diferida los contenedores, blobs, tablas y colas y consultar las entidades de forma diferida

- [API de OneDrive](https://dev.onedrive.com/README.htm)

   La API de OneDrive proporciona un conjunto de servicios HTTP que se va a conectar la aplicación a los archivos y carpetas en Office 365 y SharePoint Server 2016.

- [SDK de REST de C++ (nombre código "Casablanca")](https://github.com/Microsoft/cpprestsdk)

   Proporciona una API moderna, asincrónica y multiplataforma para interactuar con los servicios REST.

  - Realizar llamadas REST frente a cualquier servidor HTTP, con compatibilidad integrada para el documento JSON de análisis y serialización
  - Es compatible con OAuth 1 y 2, incluido un agente de escucha de redirección local
  - Realizar conexiones Websockets con servicios remotos
  - Una tarea asincrónica totalmente API basada en PPL, incluyendo un subproceso de threadpool integrado

   Es compatible con el escritorio de Windows (7 +), Windows Server (2012 y versiones posteriores), plataforma Universal de Windows, Linux, OSX, Android y iOS. 

- [Windows::Web::Http::HttpClient](https://msdn.microsoft.com/en-us/library/windows/apps/windows.web.http.httpclient.aspx)

   Una clase de cliente HTTP de Windows en tiempo de ejecución modelada en la clase .NET Framework del mismo nombre en el espacio de nombres System.Web. `HttpClient` es totalmente compatible con la carga y descarga asincrónica a través de HTTP y con los filtros de canalización que habilitan la inserción de controladores HTTP personalizados en la canalización. Windows SDK incluye filtros de ejemplo para redes de uso medido y autenticación de OAuth, entre otros. Para las aplicaciones que tienen como destino la plataforma Universal de Windows, se recomienda que use el `Windows::Web:HttpClient` clase. 

- [Interfaz IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

   Proporciona una interfaz COM nativa que puede usar en aplicaciones de Windows Runtime o aplicaciones de escritorio de Windows para conectarse a Internet a través de HTTP y emitir comandos GET, PUT y otros comandos HTTP. Para obtener más información, consulte [Tutorial: conectar usando tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](http://msdn.microsoft.com/library/windows/desktop/aa385331\(v=vs.85\).aspx)

   API de Windows que se puede utilizar en aplicaciones de escritorio de Windows para conectarse a Internet.

## <a name="see-also"></a>Vea también

[Visual C++](../visual-cpp-in-visual-studio.md) <br/>
[Redes y servicios web](/windows/uwp/networking/)
