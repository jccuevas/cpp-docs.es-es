---
title: "C&#243;mo simplifica WinInet la creaci&#243;n de aplicaciones cliente de Internet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Windows Sockets [C++], frente a WinInet"
  - "WinInet (clases), aplicaciones cliente de Internet"
  - "WinInet (clases), frente a WinSock"
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# C&#243;mo simplifica WinInet la creaci&#243;n de aplicaciones cliente de Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las extensiones de Internet para Win32, o WinInet, proporcionan acceso a los protocolos de Internet comunes, incluidos gopher, FTP, y HTTP.  Mediante WinInet, puede escribir aplicaciones cliente de internet en un nivel alto de programación, sin tener que tratar WinSock, de TCP\/IP, o detalles de protocolos de Internet concretos.  WinInet proporciona un conjunto coherente de funciones para los tres protocolos, con una interfaz conocida de la API Win32.  Esta coherencia minimiza cambios de código que debe realizar si los cambios subyacentes de protocolo \(por ejemplo, FTP al HTTP\).  
  
 Visual C\+\+ proporciona dos maneras de utilizar WinInet.  Puede llamar a funciones de internet de Win32 \(vea directamente la documentación\) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] para obtener más información\) o puede utilizar WinInet con [Clases de MFC WinInet](../mfc/mfc-classes-for-creating-internet-client-applications.md).  
  
 **Puede utilizar WinInet:**  
  
-   Páginas HTML de descarga.  
  
     El HTTP es un protocolo utilizado para transferir las páginas HTML de un servidor a un explorador cliente.  
  
-   Envíe las solicitudes de FTP para cargar o descargar archivos o para obtener listas de directorios.  
  
     Una solicitud típica es un inicio de sesión anónimo para descargar un archivo.  
  
-   Utilice el sistema del menú de gopher para obtener acceso a los recursos de internet.  
  
     Los elementos de menú pueden ser varios tipos, incluidos otros menús, una base de datos indizados que puede buscar, un grupo de noticias, o un archivo.  
  
 Para los tres protocolos, establezca una conexión, realiza solicitudes al servidor, y cierra la conexión.  
  
 **Las clases de MFC WinInet facilitan la:**  
  
-   Leer la información de HTTP, FTP, y servidores gopher tan fácilmente como archivos de lectura de un disco duro.  
  
-   Use HTTP, FTP, y los protocolos de gopher sin programación directamente el WinSock o a TCP\/IP.  
  
     Los desarrolladores que utilizan funciones internet de Win32 no deben estar familiarizados con TCP\/IP o Windows Sockets.  Todavía puede programar en el nivel de socket, mediante WinSock y protocolos TCP\/IP directamente, pero es incluso más fácil de utilizar las clases de MFC WinInet para tener acceso a HTTP, a FTP, y los protocolos de gopher a través de Internet.  Para muchas operaciones comunes, los programadores no necesitan conocer los detalles del protocolo determinado que está utilizando.  
  
 Muchas operaciones que se pueden realizar por equipo como cliente a otros equipos en internet pueden tardar mucho tiempo.  La velocidad de estas operaciones es limitada normalmente por la velocidad de red, pero también pueden verse afectadas por el otro el tráfico de red y la complejidad de la operación.  La conexión con un servidor FTP remoto, por ejemplo, requiere que el equipo primero busca el nombre de ese servidor para encontrar su dirección.  La aplicación a intentará conectarse al servidor en esa dirección.  Una vez que se abra la conexión, el equipo y el servidor remoto iniciarán una conversación con el File transferencia antes de poder utilizar realmente la conexión a los archivos de recuperación.  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Cómo simplifica MFC la creación de aplicaciones cliente de Internet](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)