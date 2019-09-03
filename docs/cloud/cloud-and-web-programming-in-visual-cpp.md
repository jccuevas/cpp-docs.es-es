---
title: Programación web y para la nube en Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: landing-page
ms.openlocfilehash: cf638bb42985fd22f7befea02c1c893387ce98c8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218507"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Programación web y para la nube en Visual C++

En C++, existen varias opciones para conectarse a la Web y a la nube.

## <a name="microsoft-azure-sdks-and-rest-services"></a>SDK y servicios REST de Microsoft Azure

- [Biblioteca de cliente de Microsoft Azure Storage para C++](https://azure.github.io/azure-storage-cpp/)

  La biblioteca de cliente de Microsoft Azure Storage para C++ proporciona una API completa para trabajar con Azure Storage, que incluye las funcionalidades siguientes, entre otras:

  - Crear, leer, eliminar y enumerar contenedores de blobs, tablas y colas.
  - Crear, leer, eliminar, enumerar y copiar blobs, así como leer y escribir intervalos de blobs.
  - Insertar, eliminar, reemplazar, combinar y consultar entidades en una tabla de Azure.
  - Poner mensajes en una cola de Azure y quitarlos de ella.
  - Enumerar de forma diferida contenedores, blobs, tablas y colas, así como consultar entidades de forma diferida.

- Los [SDK de Azure IoT Hub](/azure/iot-hub/iot-hub-devguide-sdks) ANSI C99 para el Internet de las cosas permiten a las aplicaciones IoT ejecutarse en el dispositivo o en el back-end.

- [OneDrive y SharePoint en Microsoft Graph](https://dev.onedrive.com/README.htm)

  La API de OneDrive proporciona un conjunto de servicios HTTP para conectar la aplicación a archivos y carpetas de Office 365 y SharePoint Server 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>API de redes multiplataforma y Windows

- [SDK REST de C++ (nombre de código "Casablanca")](https://github.com/Microsoft/cpprestsdk)

  Proporciona una API moderna, multiplataforma y asincrónica para interactuar con servicios REST.

  - Realiza llamadas REST a cualquier servidor HTTP, con compatibilidad integrada con la serialización y el análisis de documentos JSON.
  - Es compatible con OAuth 1 y 2, incluido un agente de escucha de redireccionamiento local.
  - Realiza conexiones WebSockets con servicios remotos.
  - API de trabajo totalmente asincrónica basada en PPL, con un grupo de subprocesos integrado.

  Es compatible con el escritorio de Windows (7 y versiones posteriores), Windows Server (2012 y versiones posteriores), Plataforma universal de Windows, Linux, OSX, Android e iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Una clase de cliente HTTP de Windows en tiempo de ejecución modelada en la clase .NET Framework del mismo nombre en el espacio de nombres System.Web. `HttpClient` es totalmente compatible con la carga y descarga asincrónica a través de HTTP y con los filtros de canalización que habilitan la inserción de controladores HTTP personalizados en la canalización. Windows SDK incluye filtros de ejemplo para redes de uso medido y autenticación de OAuth, entre otros. Para las aplicaciones que tienen como destino la Plataforma universal de Windows, se recomienda que use la clase `Windows::Web:HttpClient`.

- [Interfaz IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Proporciona una interfaz COM nativa que se puede usar en aplicaciones de Windows Runtime o en aplicaciones de escritorio de Windows para conectarse a Internet a través de HTTP y emitir comandos GET, PUT y otros comandos HTTP. Para obtener más información, vea [Tutorial: conexión con tareas y solicitudes HTTP XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/win32/WinInet/portal)

  API de Windows que se puede utilizar en aplicaciones de escritorio de Windows para conectarse a Internet.

## <a name="see-also"></a>Vea también

[C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Centro para desarrolladores de C y C++ de Microsoft Azure](https://azure.microsoft.com/develop/cpp/) <br/>
[Redes y servicios web (UWP)](/windows/uwp/networking/)
