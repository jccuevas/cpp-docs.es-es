---
title: "CHttpConnection Class | Microsoft Docs"
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
  - "CHttpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpConnection class"
  - "conectar a servidores"
  - "conectar a servidores, servidores HTTP"
  - "conexiones [C++], HTTP"
  - "conexiones HTTP"
  - "servidores HTTP, conectar"
  - "Internet connections, HTTP"
  - "Internet protocols"
  - "Internet protocols, HTTP"
  - "Internet server, HTTP"
  - "protocols, HTTP"
  - "servidores, conectar"
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHttpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

administra la conexión a un servidor HTTP.  
  
## Sintaxis  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHttpConnection::CHttpConnection](../Topic/CHttpConnection::CHttpConnection.md)|Crea un objeto `CHttpConnection`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)|Abra una solicitud HTTP.|  
  
## Comentarios  
 El HTTP es uno de tres protocolos de servidor de Internet implementados por clases MFC WinInet.  
  
 La clase `CHttpConnection` contiene un constructor y una función miembro, [OpenRequest](../Topic/CHttpConnection::OpenRequest.md), que administra conexiones a un servidor mediante un protocolo HTTP.  
  
 Para comunicarse con un servidor HTTP, debe crear primero una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md), y crea un objeto de [CHttpConnection](#_mfc_chttpconnection) .  Nunca se crea un objeto de `CHttpConnection` directamente; en su lugar, llamada [CInternetSession:: GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md), que crea el objeto de `CHttpConnection` y devuelve un puntero al.  
  
 Para obtener más información sobre cómo `CHttpConnection` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  Para obtener más información sobre cómo conectarse a los servidores mediante los otros dos protocolos de Internet compatibles, gopher y FTP, vea a clases [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)