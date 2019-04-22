---
title: Programación web y para la nube en Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 33431a8f8660af683ed2e39e10811c22fe2f4fcc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773091"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programación web y para la nube en Visual C++

En C++, existen varias opciones para conectarse a la Web y a la nube.

## <a name="cloud-programming-options"></a>Opciones de programación de nube

- [Servicios móviles de Microsoft Azure](http://www.windowsazure.com/develop/mobile/)

  Proporciona las API nativas que puede usar en aplicaciones de plataforma Universal de Windows (UWP) o aplicaciones de escritorio de Windows para conectarse a Microsoft Azure Mobile Services. Aunque la mayoría de los ejemplos del sitio web están en C#, también se puede utilizar C++. Para obtener más información, vea [Inicio rápido: Agregar un servicio móvil mediante C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

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

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Una clase de cliente HTTP de Windows en tiempo de ejecución modelada en la clase .NET Framework del mismo nombre en el espacio de nombres System.Web. `HttpClient` es totalmente compatible con la carga y descarga asincrónica a través de HTTP y con los filtros de canalización que habilitan la inserción de controladores HTTP personalizados en la canalización. Windows SDK incluye filtros de ejemplo para redes de uso medido y autenticación de OAuth, entre otros. Para las aplicaciones que tienen como destino la plataforma Universal de Windows, se recomienda que use el `Windows::Web:HttpClient` clase.

- [Interfaz IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Proporciona una interfaz COM nativa que puede usar en aplicaciones de Windows Runtime o aplicaciones de escritorio de Windows para conectarse a Internet a través de HTTP y emitir comandos GET, PUT y otros comandos HTTP. Para obtener más información, vea [Tutorial: Conectar usando tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  API de Windows que se puede utilizar en aplicaciones de escritorio de Windows para conectarse a Internet.

## <a name="see-also"></a>Vea también

[Visual C++](../overview/visual-cpp-in-visual-studio.md) <br/>
[Redes y servicios web](/windows/uwp/networking/)
