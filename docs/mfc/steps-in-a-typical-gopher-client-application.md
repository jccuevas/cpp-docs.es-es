---
title: "Pasos de una aplicaci&#243;n cliente gopher t&#237;pica | Microsoft Docs"
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
  - "aplicaciones cliente gopher"
  - "aplicaciones de Internet, aplicaciones cliente gopher"
  - "aplicaciones cliente de Internet, tabla gopher"
  - "WinInet (clases), gopher"
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Pasos de una aplicaci&#243;n cliente gopher t&#237;pica
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra los pasos que se pueden realizar en una aplicación cliente típica de gopher.  
  
|El objetivo|Las acciones que se llevan|Efectos|  
|-----------------|--------------------------------|-------------|  
|Inicia una sesión de gopher.|Cree un objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Inicializa WinInet y conecta con el servidor.|  
|Conectarse a un servidor gopher.|Uso [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md).|Devuelve un objeto de [CGopherConnection](../mfc/reference/cgopherconnection-class.md) .|  
|Busque el primer recurso en gopher.|Uso [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md).|Encuentra el primer archivo.  Devuelve FALSE si no se encuentra ningún archivo.|  
|Busque el recurso siguiente en gopher.|Uso [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md).|Busque el archivo siguiente.  Devuelve FALSE si no se encuentra el archivo.|  
|Abra el archivo situado por **FindFile** o `FindNextFile` para leer.|Obtenga un localizador de gopher mediante [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md).  Uso [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md).|Abra el archivo especificado por el atributo locator.  `OpenFile` devuelve un objeto de [CGopherFile](../mfc/reference/cgopherfile-class.md) .|  
|Abra un archivo mediante una llamada de gopher especificados.|Cree un localizador de gopher mediante [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md).  Uso [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md).|Abra el archivo especificado por el atributo locator.  `OpenFile` devuelve un objeto de [CGopherFile](../mfc/reference/cgopherfile-class.md) .|  
|Lectura del archivo.|Uso [CGopherFile](../mfc/reference/cgopherfile-class.md).|Lee el número de bytes especificado, utilizando un búfer especificados.|  
|Control de excepciones.|Utilice la clase de [CInternetException](../mfc/reference/cinternetexception-class.md) .|Controla todos los tipos de excepciones comunes de internet.|  
|Finalice la sesión de gopher.|Elimine del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Automáticamente limpia los identificadores de archivos abiertos y conexiones.|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)