---
title: "CSocketAddr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSocketAddr"
  - "ATL.CSocketAddr"
  - "ATL::CSocketAddr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSocketAddr class"
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSocketAddr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para convertir nombres de host direcciones host, admitiendo IPv4 y formatos de IPV6.  
  
## Sintaxis  
  
```  
  
class CSocketAddr  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSocketAddr::CSocketAddr](../Topic/CSocketAddr::CSocketAddr.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSocketAddr::FindAddr](../Topic/CSocketAddr::FindAddr.md)|Llame a este método para convertir el nombre de host proporcionado a la dirección del host.|  
|[CSocketAddr::FindINET4Addr](../Topic/CSocketAddr::FindINET4Addr.md)|Llame a este método para convertir el nombre de host IPv4 la dirección del host.|  
|[CSocketAddr::FindINET6Addr](../Topic/CSocketAddr::FindINET6Addr.md)|Llame a este método para convertir el nombre de host IPv6 la dirección del host.|  
|[CSocketAddr::GetAddrInfo](../Topic/CSocketAddr::GetAddrInfo.md)|Llame a este método para devolver un puntero a un elemento específico en la lista de **addrinfo** .|  
|[CSocketAddr::GetAddrInfoList](../Topic/CSocketAddr::GetAddrInfoList.md)|Llame a este método para devolver un puntero a la lista de **addrinfo** .|  
  
## Comentarios  
 Esta clase proporciona una versión de IP enfoque válido para buscar las direcciones de red para el uso con contenedores de las funciones de la API y socket de Windows Sockets en bibliotecas.  
  
 Los miembros de esta clase que se utilizan para buscar direcciones de red utilizan la función [getaddrinfo](http://msdn.microsoft.com/library/windows/desktop/ms738520)de la API Win32.  
  
 Esta clase admite a ambas direcciones de red de IPv4 andIPv6.  
  
## Requisitos  
 **encabezado:** atlsocket.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)