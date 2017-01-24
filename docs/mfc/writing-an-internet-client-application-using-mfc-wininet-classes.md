---
title: "Escribir una aplicaci&#243;n cliente de Internet mediante clases WinInet de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de Internet, aplicaciones cliente"
  - "aplicaciones de Internet, WinInet"
  - "aplicaciones cliente de Internet"
  - "aplicaciones cliente de Internet, escribir"
  - "MFC, aplicaciones de Internet"
  - "WinInet (clases), programar"
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Escribir una aplicaci&#243;n cliente de Internet mediante clases WinInet de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Base de cada aplicación cliente de internet es la sesión de internet.  MFC implementa sesiones de internet como objetos de la clase [CInternetSession](../mfc/reference/cinternetsession-class.md).  Con esta clase, puede crear una sesión de internet o a varias sesiones simultáneas.  
  
 Para comunicarse con un servidor, necesita un objeto de [CInternetConnection](../mfc/reference/cinternetconnection-class.md) así como `CInternetSession`.  Puede crear `CInternetConnection` mediante [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md), [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md), o [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md).  Cada una de estas llamadas es específica del tipo de protocolo.  Estas llamadas no abra un archivo en el servidor para lectura o escritura.  Si desea leer o escribir datos, debe abrir el archivo como un paso independiente.  
  
 Para la mayoría de las sesiones de internet, el objeto de `CInternetSession` funciona a mano con un objeto de [CInternetFile](../mfc/reference/cinternetfile-class.md) :  
  
-   Para una sesión de internet, debe crear una instancia de [CInternetSession](../mfc/reference/cinternetsession-class.md).  
  
-   Si la sesión de internet lee o escribe datos, debe crear una instancia de `CInternetFile` \(o sus subclases, [CHttpFile](../mfc/reference/chttpfile-class.md) o [CGopherFile](../mfc/reference/cgopherfile-class.md)\).  La manera más fácil de leer datos es llamar [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md).  Esta función analiza un localizador \(URL\) de recursos \(URI\) proporcionado por usted, abra una conexión al servidor especificado por la dirección URL, y devuelve un objeto de solo lectura de `CInternetFile` .  `CInternetSession::OpenURL` no es específico de un tipo de protocolo — llamada funciona para cualquier FTP, HTTP, o dirección URL de gopher.  `CInternetSession::OpenURL` incluso trabaja con archivos locales \(que devuelven `CStdioFile` en lugar de `CInternetFile`\).  
  
-   Si la sesión de internet no lee o no escribe los datos, pero realiza otras tareas, como eliminar un archivo en un directorio FTP, puede que no sea necesario crear una instancia de `CInternetFile`.  
  
 Hay dos maneras de crear un objeto de `CInternetFile` :  
  
-   Si utiliza `CInternetSession::OpenURL` para establecer la conexión al servidor, la llamada a `OpenURL` devuelve `CStdioFile`.  
  
-   Si el uso **CInternetSession::GetFtpConnection**, `GetGopherConnection`, o `GetHttpConnection` de establecer la conexión al servidor, debe llamar a `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, o **CHttpConnection::OpenRequest,** respectivamente, devolver `CInternetFile`, `CGopherFile`, o `CHttpFile`, respectivamente.  
  
 Los pasos de implementar una aplicación cliente de internet varían dependiendo de si se crea un cliente genérico de internet basado en **OpenURL** o funciona un cliente protocolo\- concreto utilizando uno de **GetConnection** .  
  
## ¿Sobre qué desea obtener más información?  
  
-   [¿Cómo escribo una aplicación cliente de internet que funcione genéricamente mediante FTP, HTTP, y gopher?](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [¿Cómo escribo una aplicación de cliente FTP que abre un archivo?](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [¿Cómo escribo una aplicación de cliente FTP que lo haga no abierto un archivo pero efectúo una operación de directorio, como eliminar un archivo?](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [¿Cómo escribo una aplicación cliente de gopher?](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [¿Cómo escribo una aplicación de cliente HTTP?](../mfc/steps-in-a-typical-http-client-application.md)  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Clases de MFC para crear aplicaciones cliente de Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)