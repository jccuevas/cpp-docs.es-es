---
title: Cómo simplifica WinInet la creación de aplicaciones cliente de Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 54f63da7451dfef39a33e6b437be938cb1652326
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624570"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica WinInet la creación de aplicaciones cliente de Internet

Las extensiones de Internet de Win32, o WinInet, proporcionan acceso a los protocolos de Internet comunes, como Gopher, FTP y HTTP. Con WinInet, puede escribir aplicaciones cliente de Internet en un nivel más alto de programación, sin tener que tratar con WinSock, TCP/IP o con los detalles de protocolos de Internet específicos. WinInet proporciona un conjunto coherente de funciones para los tres protocolos, con una interfaz de API Win32 conocida. Esta coherencia minimiza los cambios de código que se deben realizar si cambia el protocolo subyacente (por ejemplo, de FTP a HTTP).

Visual C++ proporciona dos maneras de usar WinInet. Puede llamar directamente a las funciones de Internet de Win32 (consulte la documentación de OLE en el Windows SDK para obtener más información) o bien puede usar WinInet a través de las [clases WinInet de MFC](mfc-classes-for-creating-internet-client-applications.md).

**Puede usar WinInet para:**

- Descargar páginas HTML.

   HTTP es un protocolo que se usa para transferir páginas HTML desde un servidor a un explorador cliente.

- Enviar solicitudes FTP para cargar o descargar archivos u obtener listas de directorios.

   Una solicitud típica es un inicio de sesión anónimo para descargar un archivo.

- Use el sistema de menús de Gopher para tener acceso a los recursos de Internet.

   Los elementos de menú pueden ser varios tipos, incluidos otros menús, una base de datos indizada en la que se puede buscar, un grupo de noticias o un archivo.

En el caso de los tres protocolos, establezca una conexión, realice solicitudes al servidor y cierre la conexión.

**Las clases WinInet de MFC facilitan:**

- Lea la información de los servidores HTTP, FTP y Gopher tan fácilmente como leer archivos de una unidad de disco duro.

- Use los protocolos HTTP, FTP y Gopher sin programar directamente en WinSock o TCP/IP.

   No es necesario que los desarrolladores que usan las funciones de Internet de Win32 estén familiarizados con TCP/IP o Windows Sockets. Todavía puede programar en el nivel de socket, mediante los protocolos WinSock y TCP/IP directamente, pero es aún más fácil usar las clases WinInet de MFC para tener acceso a los protocolos HTTP, FTP y Gopher a través de Internet. Para muchas operaciones comunes, los desarrolladores no necesitan conocer los detalles del protocolo concreto que usan.

Muchas operaciones que puede realizar el equipo como cliente en otros equipos de Internet pueden tardar mucho tiempo. La velocidad de estas operaciones suele estar limitada por la velocidad de la conexión de red, pero también puede verse afectada por otro tráfico de red y la complejidad de la operación. La conexión a un servidor FTP remoto, por ejemplo, requiere que el equipo busque primero el nombre de ese servidor para encontrar su dirección. A continuación, la aplicación intentará conectarse al servidor en esa dirección. Una vez abierta la conexión, el equipo y el servidor remoto iniciarán una conversación con el protocolo de transferencia de archivos antes de poder usar la conexión para recuperar archivos.

## <a name="see-also"></a>Consulte también

[Extensiones de Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Cómo simplifica MFC la creación de aplicaciones cliente de Internet](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
