---
title: "CComCritSecLock Class | Microsoft Docs"
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
  - "ATL::CComCritSecLock"
  - "ATL.CComCritSecLock<TLock>"
  - "ATL::CComCritSecLock<TLock>"
  - "ATL.CComCritSecLock"
  - "CComCritSecLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCritSecLock class"
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCritSecLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona los métodos para bloquear y desbloquear un objeto de sección crítica.  
  
## Sintaxis  
  
```  
  
      template<  
   class TLock  
> class CComCritSecLock  
```  
  
#### Parámetros  
 *TLock*  
 El objeto que se bloqueará y desbloqueado.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::CComCritSecLock](../Topic/CComCritSecLock::CComCritSecLock.md)|el constructor.|  
|[CComCritSecLock::~CComCritSecLock](../Topic/CComCritSecLock::~CComCritSecLock.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCritSecLock::Lock](../Topic/CComCritSecLock::Lock.md)|Llame a este método para bloquear el objeto de sección crítica.|  
|[CComCritSecLock::Unlock](../Topic/CComCritSecLock::Unlock.md)|Llame a este método para desbloquear el objeto de sección crítica.|  
  
## Comentarios  
 Utilice esta clase para bloquear y desbloquear objetos de una manera más segura que con [clase de CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) o [clase de CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)