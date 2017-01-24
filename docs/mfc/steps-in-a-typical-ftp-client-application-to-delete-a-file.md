---
title: "Pasos de una aplicaci&#243;n cliente FTP t&#237;pica para eliminar un archivo | Microsoft Docs"
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
  - "FTP (Protocolo de transferencia de archivos), aplicaciones cliente"
  - "aplicaciones de Internet, aplicaciones cliente FTP"
  - "aplicaciones cliente de Internet, eliminar FTP"
  - "WinInet (clases), FTP"
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Pasos de una aplicaci&#243;n cliente FTP t&#237;pica para eliminar un archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra los pasos que se pueden realizar en una aplicación de cliente FTP típica que elimina un archivo.  
  
|El objetivo|Las acciones que se llevan|Efectos|  
|-----------------|--------------------------------|-------------|  
|Inicia una sesión FTP.|Cree un objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Inicializa WinInet y conecta con el servidor.|  
|Conectarse a un servidor FTP.|Uso [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md).|Devuelve un objeto de [CFtpConnection](../mfc/reference/cftpconnection-class.md) .|  
|La comprobación para asegurarse de que está en el directorio correcto en el servidor FTP.|Uso [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md) o [CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md).|Devuelve el nombre o la dirección url del directorio que está conectado actualmente en el servidor, dependiendo de la función miembro seleccionada.|  
|Cambie a FTP un directorio en el servidor.|Uso [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md).|Cambia el directorio que está conectado actualmente en el servidor.|  
|Busque el primer archivo del directorio FTP.|Uso [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md).|Encuentra el primer archivo.  Devuelve FALSE si no se encuentra ningún archivo.|  
|Busque el archivo siguiente en el directorio FTP.|Uso [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md).|Busque el archivo siguiente.  Devuelve FALSE si no se encuentra el archivo.|  
|Elimine el archivo situado por **FindFile** o `FindNextFile`.|Utilice [CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md), utilizando el nombre de archivo devuelto por **FindFile** o `FindNextFile`.|Elimina el archivo en el servidor para lectura o escritura.|  
|Control de excepciones.|Utilice la clase de [CInternetException](../mfc/reference/cinternetexception-class.md) .|Controla todos los tipos de excepciones comunes de internet.|  
|Finalice la sesión FTP.|Elimine del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Automáticamente limpia los identificadores de archivos abiertos y conexiones.|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)