---
title: "Pasos de una aplicaci&#243;n cliente de Internet t&#237;pica | Microsoft Docs"
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
  - "aplicaciones de Internet, aplicaciones cliente"
  - "aplicaciones cliente de Internet, tabla general"
  - "WinInet (clases), programar"
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Pasos de una aplicaci&#243;n cliente de Internet t&#237;pica
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra los pasos que se pueden realizar en una aplicación cliente típica de internet.  
  
|El objetivo|Las acciones que se llevan|Efectos|  
|-----------------|--------------------------------|-------------|  
|Inicia una sesión de internet.|Cree un objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Inicializa WinInet y conecta con el servidor.|  
|Establezca una opción de consulta de internet \(límite de tiempo de espera o el número de intentos, por ejemplo\).|Uso [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md).|Devuelve FALSE si la operación fue incorrecta.|  
|Establezca una función de devolución de llamada para supervisar el estado de sesión.|Uso [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md).|Establece una devolución de llamada a [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md).  Reemplace `OnStatusCallback` para crear dispone de la rutina de devolución de llamada.|  
|Conectarse a un servidor de Internet, un servidor de intranet, o a un archivo local.|Uso [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md).|Analiza la dirección URL y abra una conexión al servidor especificado.  Devuelve [CStdioFile](../mfc/reference/cstdiofile-class.md) \(si pasa `OpenURL` un nombre de archivo local\).  Éste es el objeto al que se tiene acceso a los datos recuperados del servidor o del archivo.|  
|Lectura del archivo.|Uso [CInternetFile::Read](../Topic/CInternetFile::Read.md).|Lee el número de bytes especificado utilizando un búfer especificados.|  
|Control de excepciones.|Utilice la clase de [CInternetException](../mfc/reference/cinternetexception-class.md) .|Controla todos los tipos de excepciones comunes de internet.|  
|Finalice la sesión de internet.|Elimine del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Automáticamente limpia los identificadores de archivos abiertos y conexiones.|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)