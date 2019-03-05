---
title: Escribir una aplicación cliente de Internet mediante clases WinInet de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 6e32210217321e4eb59d7d3e666a4f5494eb3642
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287705"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Escribir una aplicación cliente de Internet mediante clases WinInet de MFC

La base de todas las aplicaciones cliente Internet es la sesión de Internet. MFC implementa las sesiones de Internet como objetos de clase [CInternetSession](../mfc/reference/cinternetsession-class.md). Esta clase puede crear una sesión de Internet o varias sesiones simultáneas.

Para comunicarse con un servidor, necesita un [CInternetConnection](../mfc/reference/cinternetconnection-class.md) objeto, así como un `CInternetSession`. Puede crear un `CInternetConnection` utilizando [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession:: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), o [CInternetSession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Cada una de estas llamadas es específica del tipo de protocolo. Estas llamadas no abra un archivo en el servidor de lectura o escritura. Si desea leer o escribir datos, debe abrir el archivo como un paso independiente.

Para la mayoría de las sesiones de Internet, el `CInternetSession` objeto funciona de la mano con un [CInternetFile](../mfc/reference/cinternetfile-class.md) objeto:

- Para una sesión de Internet, debe crear una instancia de [CInternetSession](../mfc/reference/cinternetsession-class.md).

- Si la sesión de Internet lee o escribe datos, debe crear una instancia de `CInternetFile` (o sus subclases [CHttpFile](../mfc/reference/chttpfile-class.md) o [CGopherFile](../mfc/reference/cgopherfile-class.md)). La manera más fácil de leer los datos es llamar a [CInternetSession:: OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Esta función analiza un localizador de recursos Universal (URL) proporcionado por el usuario, se abre una conexión con el servidor especificado por la dirección URL y devuelve solo lectura `CInternetFile` objeto. `CInternetSession::OpenURL` no es específico de un tipo de protocolo, la misma llamada funciona para cualquier dirección URL de FTP, HTTP o gopher. `CInternetSession::OpenURL` También funciona con archivos locales (devolviendo un `CStdioFile` en lugar de un `CInternetFile`).

- Si la sesión no leer o escribir datos, de Internet, pero realiza otras tareas, como la eliminación de un archivo en un directorio FTP, es posible que no deberá crear una instancia de `CInternetFile`.

Hay dos maneras de crear un `CInternetFile` objeto:

- Si usas `CInternetSession::OpenURL` para establecer la conexión al servidor, la llamada a `OpenURL` devuelve un `CStdioFile`.

- Si usa `CInternetSession::GetFtpConnection`, `GetGopherConnection`, o `GetHttpConnection` para establecer la conexión al servidor, debe llamar a `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, o `CHttpConnection::OpenRequest`, respectivamente, para devolver un `CInternetFile`, `CGopherFile`, o `CHttpFile`, respectivamente.

Los pasos para implementar una aplicación de cliente Internet varían dependiendo de si crea un cliente de Internet genérico basado en `OpenURL` o un cliente específico del protocolo mediante uno de los `GetConnection` funciones.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Cómo se puede escribir una aplicación de cliente de Internet que funcione genéricamente con FTP, HTTP y gopher](../mfc/steps-in-a-typical-internet-client-application.md)

- [Cómo se puede escribir una aplicación de cliente FTP que se abre un archivo](../mfc/steps-in-a-typical-ftp-client-application.md)

- [Cómo se puede escribir una aplicación de cliente FTP que realiza una operación de directorio, como la eliminación de un archivo pero que no se abre un archivo](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Cómo se puede escribir una aplicación cliente gopher](../mfc/steps-in-a-typical-gopher-client-application.md)

- [Cómo se puede escribir una aplicación de cliente HTTP](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Clases MFC para crear aplicaciones cliente de Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)
