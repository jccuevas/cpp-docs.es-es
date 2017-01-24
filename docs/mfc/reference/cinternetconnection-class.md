---
title: "CInternetConnection Class | Microsoft Docs"
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
  - "CInternetConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous connections"
  - "CInternetConnection class"
  - "Internet connections"
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

administra la conexión a un servidor de Internet.  
  
## Sintaxis  
  
```  
class CInternetConnection : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetConnection::CInternetConnection](../Topic/CInternetConnection::CInternetConnection.md)|Crea un objeto `CInternetConnection`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetConnection::GetContext](../Topic/CInternetConnection::GetContext.md)|Obtiene el Id. de contexto para este objeto de conexión.|  
|[CInternetConnection::GetServerName](../Topic/CInternetConnection::GetServerName.md)|Obtiene el nombre del servidor asociado a la conexión.|  
|[CInternetConnection::GetSession](../Topic/CInternetConnection::GetSession.md)|Obtiene un puntero al objeto de [CInternetSession](../../mfc/reference/cinternetsession-class.md) asociado a la conexión.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](../Topic/CInternetConnection::operator%20HINTERNET.md)|Identificador de una sesión de internet.|  
  
## Comentarios  
 Es la clase base para las clases MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), y [CGopherConnection](../../mfc/reference/cgopherconnection-class.md).  Cada una de estas clases proporciona funcionalidad adicional para comunicarse con FTP, el HTTP, o el servidor gopher respectivo.  
  
 Comunicarse directamente con un servidor de Internet, debe tener un objeto de [CInternetSession](../../mfc/reference/cinternetsession-class.md) y un objeto de `CInternetConnection` .  
  
 Para obtener más información sobre cómo funcionan las clases WinInet, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)