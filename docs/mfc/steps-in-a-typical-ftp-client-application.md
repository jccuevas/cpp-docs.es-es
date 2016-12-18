---
title: "Pasos de una aplicaci&#243;n cliente FTP t&#237;pica | Microsoft Docs"
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
  - "FTP (Protocolo de transferencia de archivos)"
  - "FTP (Protocolo de transferencia de archivos), aplicaciones cliente"
  - "aplicaciones de Internet, aplicaciones cliente FTP"
  - "aplicaciones cliente de Internet, FTP (table)"
  - "WinInet (clases), FTP"
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Pasos de una aplicaci&#243;n cliente FTP t&#237;pica
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación de cliente FTP típica crea [CInternetSession](../mfc/reference/cinternetsession-class.md) y un objeto de [CFtpConnection](../mfc/reference/cftpconnection-class.md) .  Observe que estas clases MFC WinInet no controlan realmente los valores del tipo de servidor proxy; IIS realiza.  
  
 También, vea estos artículos de Knowledge Base:  
  
-   HOWTO: FTP con el proxy CERN\- basado Utilizar WinInet API \(identificador de caso: Q166961\)  
  
-   EJEMPLO: FTP con el proxy protegido contraseña CERN\- basado \(identificador de caso: Q216214\)  
  
-   El Administrador de servicios Internet no puede mostrar el proxy instalado Services \(identificador de caso: Q216802\)  
  
 La tabla siguiente muestra los pasos que se pueden realizar en una aplicación de cliente FTP típica.  
  
|El objetivo|Las acciones que se llevan|Efectos|  
|-----------------|--------------------------------|-------------|  
|Inicia una sesión FTP.|Cree un objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Inicializa WinInet y conecta con el servidor.|  
|Conectarse a un servidor FTP.|Uso [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md).|Devuelve un objeto de [CFtpConnection](../mfc/reference/cftpconnection-class.md) .|  
|Cambie a FTP un directorio en el servidor.|Uso [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md).|Cambia el directorio que está conectado actualmente en el servidor.|  
|Busque el primer archivo del directorio FTP.|Uso [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md).|Encuentra el primer archivo.  Devuelve FALSE si no se encuentra ningún archivo.|  
|Busque el archivo siguiente en el directorio FTP.|Uso [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md).|Busque el archivo siguiente.  Devuelve FALSE si no se encuentra el archivo.|  
|Abra el archivo situado por **FindFile** o `FindNextFile` para lectura o escritura.|Utilice [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md), utilizando el nombre de archivo devuelto por [FindFile](../Topic/CFtpFileFind::FindFile.md) o [FindNextFile](../Topic/CFtpFileFind::FindNextFile.md).|Abra el archivo en el servidor para lectura o escritura.  Devuelve un objeto de [CInternetFile](../mfc/reference/cinternetfile-class.md) .|  
|Leer o escribir en el archivo.|Uso [CInternetFile::Read](../Topic/CInternetFile::Read.md) o [CInternetFile::Write](../Topic/CInternetFile::Write.md).|Lee o escribe el número de bytes especificado, utilizando un búfer que proporcione.|  
|Control de excepciones.|Utilice la clase de [CInternetException](../mfc/reference/cinternetexception-class.md) .|Controla todos los tipos de excepciones comunes de internet.|  
|Finalice la sesión FTP.|Elimine del objeto de [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Automáticamente limpia los identificadores de archivos abiertos y conexiones.|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Requisitos previos para las clases de cliente Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)