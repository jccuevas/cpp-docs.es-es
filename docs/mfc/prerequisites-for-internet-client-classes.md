---
title: "Requisitos previos para las clases de cliente Internet | Microsoft Docs"
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
  - "clases [C++], conexiones"
  - "conexiones [C++], para las clases"
  - "archivos [C++], leer"
  - "archivos [C++], escribir"
  - "FTP (Protocolo de transferencia de archivos), clases MFC"
  - "aplicaciones cliente gopher"
  - "requisitos previos gopher"
  - "HTTP, requisitos previos para clientes de Internet"
  - "Internet [C++], conexiones"
  - "requisitos previos para las clases de cliente de Internet [C++]"
  - "archivos de Internet [C++], escribir"
  - "requisitos previos, clases para cliente de Internet"
  - "URL [C++], aplicaciones cliente de Internet"
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Requisitos previos para las clases de cliente Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Algunas acciones realizadas por un cliente de internet \(que lee un archivo, por ejemplo\) tienen acciones de requisito previo \(en este caso, si se establece una conexión a Internet\).  Las tablas siguientes se enumeran los requisitos previos para algunas acciones de cliente.  
  
### Dirección URL general de internet \(FTP, Gopher, o HTTP\)  
  
|Acción|Requisito previo|  
|------------|----------------------|  
|Establezca una conexión.|Cree [CInternetSession](../mfc/reference/cinternetsession-class.md) para establecer la base de una aplicación cliente de internet.|  
|Abra una dirección URL.|Establezca una conexión.  Llamada [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md).  La función de `OpenURL` devuelve un objeto de solo lectura de recursos.|  
|Datos de la dirección URL de la lectura.|Abra la dirección URL.  Llamada [CInternetFile::Read](../Topic/CInternetFile::Read.md).|  
|Establezca una opción de Internet.|Establezca una conexión.  Llamada [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md).|  
|Establezca una función que se va con información de estado.|Establezca una conexión.  Llamada [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md).  Reemplazo [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) para controlar llamadas.|  
  
### FTP  
  
|Acción|Requisito previo|  
|------------|----------------------|  
|Establezca una conexión FTP.|Cree [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación cliente de internet.  Llamada [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md) para crear un objeto de [CFtpConnection](../mfc/reference/cftpconnection-class.md) .|  
|Busque el primer recurso.|Establezca una conexión FTP.  Cree un objeto de [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) .  Llamada [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md).|  
|Enumera todos los recursos disponibles.|Busque el primer archivo.  Llamada [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md) hasta que devuelve FALSE.|  
|Abra un archivo de FTP.|Establezca una conexión FTP.  Llame a [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md) para crear y abrir un objeto de [CInternetFile](../mfc/reference/cinternetfile-class.md) .|  
|Lee un archivo de FTP.|Abra un archivo de FTP con acceso de lectura.  Llamada [CInternetFile::Read](../Topic/CInternetFile::Read.md).|  
|Escribir en un archivo de FTP.|Abra un archivo de FTP con acceso de escritura.  Llamada [CInternetFile::Write](../Topic/CInternetFile::Write.md).|  
|Cambie el directorio del cliente en el servidor.|Establezca una conexión FTP.  Llamada [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md).|  
|Recupere el directorio actual del cliente en el servidor.|Establezca una conexión FTP.  Llamada [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md).|  
  
### HTTP  
  
|Acción|Requisito previo|  
|------------|----------------------|  
|Establezca una conexión HTTP.|Cree [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación cliente de internet.  Llamada [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md) para crear un objeto de [CHttpConnection](../mfc/reference/chttpconnection-class.md) .|  
|Abra un archivo de HTTP.|Establezca una conexión HTTP.  Llamada [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md) para crear un objeto de [CHttpFile](../mfc/reference/chttpfile-class.md) .  Llamada [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md).  Llamada [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md).|  
|Lee un archivo HTTP.|Abra un archivo de HTTP.  Llamada [CInternetFile::Read](../Topic/CInternetFile::Read.md).|  
|Obtiene información sobre una solicitud HTTP.|Establezca una conexión HTTP.  Llamada [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md) para crear un objeto de [CHttpFile](../mfc/reference/chttpfile-class.md) .  Llamada [CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md).|  
  
### Gopher  
  
|Acción|Requisito previo|  
|------------|----------------------|  
|Establezca una conexión de gopher.|Cree [CInternetSession](../mfc/reference/cinternetsession-class.md) como base de esta aplicación cliente de internet.  Llamada [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md) para crear [CGopherConnection](../mfc/reference/cgopherconnection-class.md).|  
|Busque el primer archivo del directorio actual.|Establezca una conexión de gopher.  Cree un objeto de [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) .  Llamada [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md) para crear un objeto de [CGopherLocator](../mfc/reference/cgopherlocator-class.md) .  Pase el localizador a [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md).  Llame a [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md) para obtener el localizador de un archivo si se necesita más adelante.|  
|Mostrar todos los archivos disponibles.|Busque el primer archivo.  Llamada [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md) hasta que devuelve FALSE.|  
|Abra un archivo de gopher.|Establezca una conexión de gopher.  Cree un localizador de gopher con [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md) o busque una llamada con [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md).  Llamada [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md).|  
|Lee un archivo de gopher.|Abra un archivo de gopher.  Uso [CGopherFile](../mfc/reference/cgopherfile-class.md).|  
  
## Vea también  
 [Extensiones de Internet Win32 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [Clases de MFC para crear aplicaciones cliente de Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Escribir una aplicación cliente de Internet mediante clases WinInet de MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)