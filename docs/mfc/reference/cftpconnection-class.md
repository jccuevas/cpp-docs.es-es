---
title: "CFtpConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFtpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpConnection class"
  - "FTP (Protocolo de transferencia de archivos), establecer conexiones"
  - "Internet connections, FTP"
  - "Internet services, FTP"
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFtpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Administra la conexión FTP a un servidor de Internet y permite la manipulación directa de directorios y archivos en ese servidor.  
  
## Sintaxis  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFtpConnection::CFtpConnection](../Topic/CFtpConnection::CFtpConnection.md)|Crea un objeto `CFtpConnection`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFtpConnection::Command](../Topic/CFtpConnection::Command.md)|envía un comando directamente a un servidor FTP.|  
|[CFtpConnection::CreateDirectory](../Topic/CFtpConnection::CreateDirectory.md)|Crea un directorio en el servidor.|  
|[CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md)|Obtiene el directorio actual para esta conexión.|  
|[CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md)|Obtiene el directorio actual para esta conexión como dirección URL.|  
|[CFtpConnection::GetFile](../Topic/CFtpConnection::GetFile.md)|Obtiene un archivo de servidor conectado|  
|[CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)|Abra un archivo en el servidor conectado.|  
|[CFtpConnection::PutFile](../Topic/CFtpConnection::PutFile.md)|Coloca un archivo en el servidor.|  
|[CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md)|Quita un archivo de servidor.|  
|[CFtpConnection::RemoveDirectory](../Topic/CFtpConnection::RemoveDirectory.md)|Quita el directorio del servidor especificado.|  
|[CFtpConnection::Rename](../Topic/CFtpConnection::Rename.md)|Cambiar el nombre de un archivo en el servidor.|  
|[CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)|Establece el directorio actual de FTP.|  
  
## Comentarios  
 FTP es uno de los tres servicios Internet reconocidos por las clases de MFC WinInet.  
  
 Para comunicarse con un servidor de Internet FTP, debe crear primero una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md), y crea un objeto de `CFtpConnection` .  Nunca se crea un objeto de `CFtpConnection` directamente; en su lugar, llamada [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md), que crea el objeto de `CFtpConnection` y devuelve un puntero al.  
  
 Para obtener más información sobre cómo `CFtpConnection` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  Para obtener más información sobre cómo comunicarse con los otros dos servicios compatibles, el HTTP y gopher, vea a clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).  
  
## Ejemplo  
 Vea el ejemplo en la información general de la clase de [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)