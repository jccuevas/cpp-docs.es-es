---
title: Cómo simplifica WinInet la creación de aplicaciones cliente de Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 6da2ef1595e525bcfd407d67c806aa80cf90f1c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262715"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica WinInet la creación de aplicaciones cliente de Internet

Las extensiones de Internet Win32 o WinInet, proporcionan acceso a los protocolos de Internet comunes, incluidos HTTP, gopher y FTP. WinInet puede escribir aplicaciones de cliente de Internet en un nivel superior de la programación, sin tener que tratar con WinSock, TCP/IP o los detalles de los protocolos de Internet específicos. WinInet proporciona un conjunto coherente de funciones para los tres protocolos, con una interfaz conocida de la API de Win32. Esta coherencia minimiza los cambios de código que deba realizar si el protocolo subyacente cambia (por ejemplo, de FTP a HTTP).

Visual C++ ofrece dos formas de usar WinInet. Puede llamar a las funciones de Internet Win32 directamente (consulte la documentación de OLE en el SDK de Windows para obtener más información) o puede usar WinInet a través de la [clases WinInet de MFC](../mfc/mfc-classes-for-creating-internet-client-applications.md).

**Puede usar WinInet para:**

- Descargar páginas HTML.

   HTTP es un protocolo utilizado para transferir las páginas HTML desde un servidor a un explorador cliente.

- Enviar solicitudes FTP para cargar o descargar archivos u obtener las listas de directorios.

   Una solicitud típica es un inicio de sesión anónimo para descargar un archivo.

- Utilice el sistema de menús de gopher para tener acceso a recursos de Internet.

   Los elementos de menú pueden ser varios tipos, incluidos otros menús, una base de datos indizada que puede buscar, un grupo de noticias o un archivo.

Para los tres protocolos, establecer una conexión, realizar solicitudes al servidor y cerrar la conexión.

**Las clases WinInet de MFC facilitan:**

- Leer información de servidores HTTP, FTP y gopher tan fácilmente como la lectura de archivos desde una unidad de disco dura.

- Use los protocolos HTTP, FTP y gopher sin programar directamente para WinSock o TCP/IP.

   Los desarrolladores que usan las funciones de Internet de Win32 no es necesario estar familiarizado con TCP/IP o Windows Sockets. Todavía puede programar en el nivel de socket mediante protocolos de WinSock y TCP/IP directamente, pero es aún más fácil usar las clases WinInet de MFC para acceso HTTP, FTP y gopher protocolos a través de Internet. Para muchas operaciones comunes, los desarrolladores no es necesario conocer los detalles de usan el protocolo en particular.

Muchas operaciones que se pueden realizar en el equipo como un cliente a otros equipos en Internet pueden tardar mucho tiempo. La velocidad de estas operaciones se ve limitada por la velocidad de la conexión de red, pero también puede verse afectados por otro tráfico de red y la complejidad de la operación. Conectarse a un servidor FTP remoto, por ejemplo, requiere que el equipo busque primero el nombre del servidor para encontrar su dirección. La aplicación intentará conectarse al servidor en esa dirección. Una vez que se abre la conexión, el equipo y el servidor remoto inician una conversación con el protocolo de transferencia de archivos para poder usar realmente la conexión para recuperar archivos.

## <a name="see-also"></a>Vea también

[Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Cómo simplifica MFC la creación de aplicaciones cliente de Internet](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)
