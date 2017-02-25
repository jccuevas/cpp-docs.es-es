---
title: "CGopherConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherConnection class"
  - "conectar a servidores"
  - "conectar a servidores, gopher servers"
  - "protocolo gopher"
  - "gopher server"
  - "Internet connections, gopher"
  - "Internet server, gopher"
  - "protocols, gopher"
  - "servidores, conectar"
  - "servicios, gopher"
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGopherConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

administra la conexión a un servidor de Internet de gopher.  
  
> [!NOTE]
>  Se han dejado de utilizar las clases `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` y sus miembros porque no funcionan en la plataforma de Windows XP, pero seguirán funcionando en plataformas anteriores.  
  
## Sintaxis  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherConnection::CGopherConnection](../Topic/CGopherConnection::CGopherConnection.md)|Crea un objeto `CGopherConnection`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)|Crea un objeto de [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) para buscar los archivos en un servidor gopher.|  
|[CGopherConnection::GetAttribute](../Topic/CGopherConnection::GetAttribute.md)|Recupera información de atributos para el objeto de gopher.|  
|[CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)|Abra un archivo de gopher.|  
  
## Comentarios  
 El servicio de gopher es uno de los tres servicios Internet reconocidos por las clases de MFC WinInet.  
  
 La clase `CGopherConnection` contiene un constructor y tres funciones miembro adicional que administren el servicio de gopher: [OpenFile](../Topic/CGopherConnection::OpenFile.md), [CreateLocator](../Topic/CGopherConnection::CreateLocator.md), y [GetAttribute](../Topic/CGopherConnection::GetAttribute.md).  
  
 Para comunicarse con un servidor de Internet de gopher, primero debe crear una instancia de [CInternetSession](../../mfc/reference/cinternetsession-class.md), y después llama [CInternetSession:: GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md), que crea el objeto de `CGopherConnection` y devuelve un puntero al.  Nunca se crea un objeto de `CGopherConnection` directamente.  
  
 Para obtener más información sobre cómo `CGopherConnection` funciona con las clases de internet de MFC, vea el artículo [Internet que programa con WinInet](../../mfc/win32-internet-extensions-wininet.md).  Para obtener más información sobre cómo utilizar los otros dos servicios Internet compatibles, FTP y el HTTP consulta a clases [CHttpConnection](../../mfc/reference/chttpconnection-class.md) y [CFtpConnection](../../mfc/reference/cftpconnection-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## Requisitos  
 **encabezado:** afxinet.h  
  
## Vea también  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)