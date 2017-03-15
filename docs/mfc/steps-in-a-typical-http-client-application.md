---
title: "Pasos de una aplicaci&#243;n cliente HTTP t&#237;pica | Microsoft Docs"
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
  - "aplicaciones [MFC], cliente HTTP"
  - "aplicaciones cliente [C++], HTTP"
  - "aplicaciones cliente HTTP"
  - "aplicaciones de Internet [C++], aplicaciones cliente HTTP"
  - "aplicaciones cliente de Internet [C++], HTTP (table)"
  - "WinInet (clases), HTTP"
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Pasos de una aplicaci&#243;n cliente HTTP t&#237;pica
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra los pasos que se pueden realizar en una aplicación de cliente HTTP típica:  
  
|El objetivo|Las acciones que se llevan|Efectos|  
|-----------------|--------------------------------|-------------|  
|Inicia una sesión HTTP.|Cree un objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Inicializa WinInet y conecta con el servidor.|  
|Conectarse a un servidor HTTP.|Uso [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md).|Devuelve un objeto de [CHttpConnection](../mfc/reference/chttpconnection-class.md) .|  
|Abra una solicitud HTTP.|Uso [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md).|Devuelve un objeto de [CHttpFile](../mfc/reference/chttpfile-class.md) .|  
|Enviar una solicitud HTTP.|Uso [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md) y [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md).|Busque el archivo.  Devuelve FALSE si no se encuentra el archivo.|  
|Lectura del archivo.|Uso [CHttpFile](../mfc/reference/chttpfile-class.md).|Lee el número de bytes especificado utilizando un búfer especificados.|  
|Control de excepciones.|Utilice la clase de [CInternetException](../mfc/reference/cinternetexception-class.md) .|Controla todos los tipos de excepciones comunes de internet.|  
|Finalice la sesión HTTP.|Elimine del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Automáticamente limpia los identificadores de archivos abiertos y conexiones.|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)