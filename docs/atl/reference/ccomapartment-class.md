---
title: "CComApartment Class | Microsoft Docs"
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
  - "ATL::CComApartment"
  - "CComApartment"
  - "ATL.CComApartment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartments in ATL EXE modules"
  - "CComApartment class"
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComApartment Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona compatibilidad para administrar un apartamento de un módulo subproceso\-reunido EXE.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CComApartment  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::CComApartment](../Topic/CComApartment::CComApartment.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::Apartment](../Topic/CComApartment::Apartment.md)|Marca la dirección inicial del subproceso.|  
|[CComApartment::GetLockCount](../Topic/CComApartment::GetLockCount.md)|Devuelve el recuento de bloqueo actual del subproceso.|  
|[CComApartment::Lock](../Topic/CComApartment::Lock.md)|Incrementa el recuento de bloqueo de subprocesos.|  
|[CComApartment::Unlock](../Topic/CComApartment::Unlock.md)|Disminuye el recuento de bloqueo de subprocesos.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComApartment::m\_dwThreadID](../Topic/CComApartment::m_dwThreadID.md)|Contiene el identificador del subproceso.|  
|[CComApartment::m\_hThread](../Topic/CComApartment::m_hThread.md)|Contiene el identificador del subproceso.|  
|[CComApartment::m\_nLockCnt](../Topic/CComApartment::m_nLockCnt.md)|Contiene el número de bloqueo actual del subproceso.|  
  
## Comentarios  
 `CComApartment` es utilizado por [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) para administrar un apartamento de un módulo subproceso\-reunido EXE.  `CComApartment` proporciona métodos para aumentar y disminuir el recuento de bloqueo en un subproceso.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)