---
title: "Clases de MFC para crear aplicaciones cliente de Internet | Microsoft Docs"
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
  - "clases [C++], MFC"
  - "aplicaciones de Internet, MFC"
  - "aplicaciones cliente de Internet, MFC"
  - "MFC, WinInet (clases)"
  - "WinInet (clases), clases"
ms.assetid: 67d34117-9839-4f4b-8bb8-0e4a9471c606
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de MFC para crear aplicaciones cliente de Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona las siguientes clases y funciones globales para escribir aplicaciones cliente de internet.  La sangría indica que una clase se deriva de la clase unindented sobre ella.  `CGopherFile` y `CHttpFile` derivan de `CInternetFile`, por ejemplo.  Estas clases y funciones globales se declaran en AFXINET.H, excepto `CFileFind`, que se declara en AFX.H.  
  
## Clases  
  
-   [CInternetSession](../mfc/reference/cinternetsession-class.md)  
  
-   [CInternetConnection](../mfc/reference/cinternetconnection-class.md)  
  
    -   [CFtpConnection](../mfc/reference/cftpconnection-class.md)  
  
    -   [CGopherConnection](../mfc/reference/cgopherconnection-class.md)  
  
    -   [CHttpConnection](../mfc/reference/chttpconnection-class.md)  
  
-   [CInternetFile](../mfc/reference/cinternetfile-class.md)  
  
    -   [CGopherFile](../mfc/reference/cgopherfile-class.md)  
  
    -   [CHttpFile](../mfc/reference/chttpfile-class.md)  
  
-   [CFileFind](../mfc/reference/cfilefind-class.md)  
  
    -   [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)  
  
    -   [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)  
  
-   [CGopherLocator](../mfc/reference/cgopherlocator-class.md)  
  
-   [CInternetException](../mfc/reference/cinternetexception-class.md)  
  
## Funciones globales  
  
-   [AfxParseURL](../Topic/AfxParseURL.md)  
  
-   [AfxGetInternetHandleType](../Topic/AfxGetInternetHandleType.md)  
  
-   [AfxThrowInternetException](../Topic/AfxThrowInternetException.md)  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)