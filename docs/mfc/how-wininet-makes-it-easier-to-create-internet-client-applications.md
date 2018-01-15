---
title: "Cómo simplifica WinInet crear aplicaciones de cliente de Internet | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9c79404f296df09afb177930897064b8455217d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Cómo simplifica WinInet la creación de aplicaciones cliente de Internet
Las extensiones de Internet Win32, o WinInet, proporcionan acceso a los protocolos de Internet comunes, incluidos HTTP, FTP y gopher. Con WinInet, puede crear aplicaciones de cliente de Internet en un nivel superior de la programación, sin tener que tratar con WinSock, TCP/IP o los detalles de los protocolos de Internet específicos. WinInet proporciona un conjunto coherente de funciones para los tres protocolos, con una interfaz conocida de la API de Win32. Esta coherencia reduce los cambios en el código que debe realizar si el protocolo subyacente cambia (por ejemplo, de FTP a HTTP).  
  
 Visual C++ proporciona dos formas de usar WinInet. Se pueden llamar a las funciones de Internet Win32 directamente (vea la documentación de OLE en el SDK de Windows para obtener más información) o puede usar WinInet a través de la [clases WinInet de MFC](../mfc/mfc-classes-for-creating-internet-client-applications.md).  
  
 **Puede usar WinInet para:**  
  
-   Descargar páginas HTML.  
  
     HTTP es un protocolo utilizado para transferir páginas HTML desde un servidor en un explorador del cliente.  
  
-   Enviar las solicitudes FTP para cargar o descargar archivos u obtener listados de directorios.  
  
     Una solicitud típica es un inicio de sesión anónimo para descargar un archivo.  
  
-   Utilice el sistema de menús de gopher para tener acceso a recursos de Internet.  
  
     Elementos de menú pueden ser varios tipos, incluidos otros menús, una base de datos indizada que puede buscar, un grupo de noticias o un archivo.  
  
 Para todos los protocolos de tres, establecer una conexión, realizar solicitudes al servidor y cerrar la conexión.  
  
 **Las clases WinInet de MFC facilitan:**  
  
-   Leer información de servidores HTTP, FTP y gopher tan fácilmente como leer archivos desde una unidad de disco duro.  
  
-   Use los protocolos HTTP, FTP y gopher sin programar directamente para WinSock o TCP/IP.  
  
     Los desarrolladores que usan las funciones de Internet de Win32 no es necesario estar familiarizado con TCP/IP o Windows Sockets. Todavía puede programar en el nivel de socket, utilizando los protocolos TCP/IP y WinSock directamente, pero es incluso más fácil de usar las clases WinInet de MFC para tener acceso a HTTP, FTP y gopher protocolos a través de Internet. Para muchas operaciones comunes, los desarrolladores no es necesario conocer los detalles de usan el protocolo en particular.  
  
 Muchas operaciones que se pueden realizar en el equipo como un cliente a otros equipos en Internet pueden tardar mucho tiempo. La velocidad de estas operaciones se ve limitada por la velocidad de la conexión de red, pero también puede verse afectados por otro tráfico de red y la complejidad de la operación. Conectarse a un servidor FTP remoto, por ejemplo, requiere que el equipo buscará primero el nombre del servidor para encontrar su dirección. La aplicación, a continuación, intentará conectarse al servidor a esa dirección. Una vez que se abre la conexión, el equipo y el servidor remoto inician una conversación con el protocolo de transferencia de archivos antes de que realmente puede usar la conexión para recuperar archivos.  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Cómo simplifica MFC la creación de aplicaciones cliente de Internet](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)

