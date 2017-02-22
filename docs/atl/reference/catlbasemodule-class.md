---
title: "CAtlBaseModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlBaseModule"
  - "ATL.CAtlBaseModule"
  - "CAtlBaseModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlBaseModule class"
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CAtlBaseModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase se crean instancias en cada proyecto ATL.  
  
## Sintaxis  
  
```  
  
   class CAtlBaseModule :  
public _ATL_BASE_MODULE  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::CAtlBaseModule](../Topic/CAtlBaseModule::CAtlBaseModule.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::AddResourceInstance](../Topic/CAtlBaseModule::AddResourceInstance.md)|Agrega una instancia de recursos a la lista de identificadores almacenados.|  
|[CAtlBaseModule::GetHInstanceAt](../Topic/CAtlBaseModule::GetHInstanceAt.md)|Devuelve un identificador a una instancia especificada del recurso.|  
|[CAtlBaseModule::GetModuleInstance](../Topic/CAtlBaseModule::GetModuleInstance.md)|Devuelve la instancia de módulos de un objeto de `CAtlBaseModule` .|  
|[CAtlBaseModule::GetResourceInstance](../Topic/CAtlBaseModule::GetResourceInstance.md)|Devuelve la instancia de un objeto de `CAtlBaseModule` .|  
|[CAtlBaseModule::RemoveResourceInstance](../Topic/CAtlBaseModule::RemoveResourceInstance.md)|Quita una instancia de la lista de identificadores almacenados.|  
|[CAtlBaseModule::SetResourceInstance](../Topic/CAtlBaseModule::SetResourceInstance.md)|Establece la instancia de un objeto de `CAtlBaseModule` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::m\_bInitFailed](../Topic/CAtlBaseModule::m_bInitFailed.md)|Una variable que indica si se ha producido un error en la inicialización del módulo.|  
  
## Comentarios  
 Una instancia de `CAtlBaseModule` llamó al \_AtlBaseModule está presente en cada proyecto ATL, que contiene un identificador de la instancia del módulo, un identificador al módulo que contenga los recursos \(que de forma predeterminada, es uno y lo mismo\), y una matriz de identificadores a los módulos que proporcionaban recursos primarios.  `CAtlBaseModule` se puede lograr con seguridad de varios subprocesos.  
  
 Esta clase reemplaza la clase obsoletos de [CComModule](../../atl/reference/ccommodule-class.md) utilizada en versiones anteriores de ATL.  
  
## Jerarquía de herencia  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md)  
  
 `CAtlBaseModule`  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)