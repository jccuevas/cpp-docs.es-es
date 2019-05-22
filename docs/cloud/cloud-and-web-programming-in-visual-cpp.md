---
title: Programación web y para la nube en Visual C++
ms.date: 11/04/2016
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.openlocfilehash: 3d71e36b6209c693940f2ebe6b5e9c73bc0c9d9d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708041"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programación web y para la nube en Visual C++

En C++, existen varias opciones para conectarse a la Web y a la nube.

## <a name="cloud-programming-options"></a>Opciones de programación de nube

- [Servicios móviles de Microsoft Azure](http://www.windowsazure.com/develop/mobile/)

  Proporciona las API nativas que se pueden usar en las aplicaciones de la Plataforma universal de Windows (UWP) o en las aplicaciones de escritorio de Windows para conectarse a Microsoft Azure Mobile Services. Aunque la mayoría de los ejemplos del sitio web están en C#, también se puede utilizar C++. Para obtener más información, vea [Inicio rápido: agregar un servicio móvil con C++](https://msdn.microsoft.com/library/windows/apps/dn263181.aspx).

- [Biblioteca de cliente de Microsoft Azure Storage para C++](https://blogs.msdn.microsoft.com/windowsazurestorage/2015/04/29/microsoft-azure-storage-client-library-for-c-v1-0-0-general-availability/)

  La biblioteca de cliente de Microsoft Azure Storage para C++ proporciona una API completa para trabajar con Azure Storage, que incluye las funcionalidades siguientes, entre otras:

  - Crear, leer, eliminar y enumerar contenedores de blobs, tablas y colas.
  - Crear, leer, eliminar, enumerar y copiar blobs, así como leer y escribir intervalos de blobs.
  - Insertar, eliminar, reemplazar, combinar y consultar entidades en una tabla de Azure.
  - Poner mensajes en una cola de Azure y quitarlos de ella.
  - Enumerar de forma diferida contenedores, blobs, tablas y colas, así como consultar entidades de forma diferida.

- [API de OneDrive](https://dev.onedrive.com/README.htm)

  La API de OneDrive proporciona un conjunto de servicios HTTP para conectar la aplicación a archivos y carpetas de Office 365 y SharePoint Server 2016.

- [SDK de REST de C++ (nombre código "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Proporciona una API moderna, multiplataforma y asincrónica para interactuar con servicios REST.

  - Realiza llamadas REST a cualquier servidor HTTP, con compatibilidad integrada con la serialización y el análisis de documentos JSON.
  - Es compatible con OAuth 1 y 2, incluido un agente de escucha de redireccionamiento local.
  - Realiza conexiones WebSockets con servicios remotos.
  - Una API de tareas totalmente asincrónica basada en PPL, con un grupo de subprocesos integrado.

  Es compatible con el escritorio de Windows (7 y versiones posteriores), Windows Server (2012 y versiones posteriores), Plataforma universal de Windows, Linux, OSX, Android e iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Una clase de cliente HTTP de Windows en tiempo de ejecución modelada en la clase .NET Framework del mismo nombre en el espacio de nombres System.Web. `HttpClient` es totalmente compatible con la carga y descarga asincrónica a través de HTTP y con los filtros de canalización que habilitan la inserción de controladores HTTP personalizados en la canalización. Windows SDK incluye filtros de ejemplo para redes de uso medido y autenticación de OAuth, entre otros. Para las aplicaciones que tienen como destino la Plataforma universal de Windows, se recomienda que use la clase `Windows::Web:HttpClient`.

- [Interfaz IXMLHTTPRequest2](/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Proporciona una interfaz COM nativa que se puede usar en aplicaciones de Windows Runtime o en aplicaciones de escritorio de Windows para conectarse a Internet a través de HTTP y emitir comandos GET, PUT y otros comandos HTTP. Para obtener más información, vea [Tutorial: conexión con tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/desktop/WinInet/portal)

  API de Windows que se puede utilizar en aplicaciones de escritorio de Windows para conectarse a Internet.

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Redes y servicios web](/windows/uwp/networking/)
