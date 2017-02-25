---
title: "C&#243;mo simplifica MFC la creaci&#243;n de aplicaciones cliente de Internet | Microsoft Docs"
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
  - "aplicaciones de Internet, MFC"
  - "aplicaciones cliente de Internet, MFC"
  - "MFC, aplicaciones de Internet"
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# C&#243;mo simplifica MFC la creaci&#243;n de aplicaciones cliente de Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Classes encapsula las funciones de extensión de Internet para Win32 \(WinInet\) de una forma que proporciona un contexto conocida para los programadores de MFC.  MFC proporciona tres tipos de archivo de Internet \([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), y [CGopherFile](../mfc/reference/cgopherfile-class.md)\) derivadas de la clase de [CStdioFile](../mfc/reference/cstdiofile-class.md) .  No solo estas clases crean el habitual de los datos de internet que recupera y manipular los programadores que han utilizado `CStdioFile` para los archivos locales, pero con estas clases puede controlar los archivos locales y los archivos de Internet de una manera coherente, transparente.  
  
 Las clases de MFC WinInet proporcionan la misma funcionalidad que `CStdioFile` para los datos que se transfieren a través de Internet.  Estas clases resumen los protocolos de Internet para HTTP, FTP, y gopher en una interfaz de programación de aplicaciones de alto nivel, proporcionando una ruta rápida y sencilla a crear aplicaciones Herramienta de creación de HTML\- con conocimiento pleno.  Por ejemplo, la conexión con un servidor FTP todavía requiere varios pasos en un nivel bajo, sino como un programador de MFC, sólo necesita realizar una llamada a `CInternetSession::GetFTPConnection` para crear dicha conexión.  
  
 Además, las clases de MFC WinInet proporcionan las ventajas siguientes:  
  
-   E\/S almacenado en búfer  
  
-   Identificadores Tipo\- seguros para datos  
  
-   Parámetros predeterminados para muchas funciones  
  
-   Control de excepciones para los errores comunes de internet  
  
-   Limpieza automática de identificadores abiertos y de conexiones  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Cómo simplifica WinInet la creación de aplicaciones cliente de Internet](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)