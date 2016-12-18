---
title: "CAutoRevertImpersonation Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAutoRevertImpersonation"
  - "CAutoRevertImpersonation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoRevertImpersonation class"
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoRevertImpersonation Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase revierte los objetos de [CAccessToken](../../atl/reference/caccesstoken-class.md) un estado nonimpersonating cuando salga del ámbito.  
  
## Sintaxis  
  
```  
  
class CAutoRevertImpersonation  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoRevertImpersonation::CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::CAutoRevertImpersonation.md)|Construye un objeto de `CAutoRevertImpersonation`|  
|[CAutoRevertImpersonation::~CAutoRevertImpersonation](../Topic/CAutoRevertImpersonation::~CAutoRevertImpersonation.md)|Destruye el objeto y revierte la suplantación del token de acceso.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAutoRevertImpersonation::Attach](../Topic/CAutoRevertImpersonation::Attach.md)|Automatiza la reversión de la suplantación de un token de acceso.|  
|[CAutoRevertImpersonation::Detach](../Topic/CAutoRevertImpersonation::Detach.md)|Cancela la reversión automática de suplantación.|  
|[CAutoRevertImpersonation::GetAccessToken](../Topic/CAutoRevertImpersonation::GetAccessToken.md)|Recupera el valor actual del token de acceso asociada a este objeto.|  
  
## Comentarios  
 [token de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374909) es un objeto que describe el contexto de seguridad de un proceso o de un subproceso y se asigna a cada usuario registrado en un sistema de Windows NT o Windows 2000.  Estos símbolos de acceso se pueden representar con la clase de `CAccessToken` .  
  
 A veces es necesario suplantar los símbolos de acceso.  Esta clase se proporciona como comodidad, pero no realiza la suplantación de símbolos de acceso; realiza sólo la reversión automática a un estado nonimpersonated.  Esto es porque la suplantación de acceso del token se puede realizar varias maneras diferentes.  
  
 Para obtener una introducción al modelo de control de acceso de Windows, vea [control de acceso](http://msdn.microsoft.com/library/windows/desktop/aa374860) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Requisitos  
 **encabezado:** atlsecurity.h  
  
## Vea también  
 [Ejemplo ATLSecurity](../../top/visual-cpp-samples.md)   
 [Access Tokens](http://msdn.microsoft.com/library/windows/desktop/aa374909)   
 [Class Overview](../../atl/atl-class-overview.md)