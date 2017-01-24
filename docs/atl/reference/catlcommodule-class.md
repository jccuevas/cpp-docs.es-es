---
title: "CAtlComModule Class | Microsoft Docs"
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
  - "ATL.CAtlComModule"
  - "CAtlComModule"
  - "ATL::CAtlComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlComModule class"
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa un módulo de servidor COM.  
  
## Sintaxis  
  
```  
  
   class CAtlComModule :  
public _ATL_COM_MODULE  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](../Topic/CAtlComModule::CAtlComModule.md)|el constructor.|  
|[CAtlComModule::~CAtlComModule](../Topic/CAtlComModule::~CAtlComModule.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](../Topic/CAtlComModule::RegisterServer.md)|Llame a este método para actualizar el registro del sistema para cada objeto del mapa del objeto.|  
|[CAtlComModule::RegisterTypeLib](../Topic/CAtlComModule::RegisterTypeLib.md)|Llame a este método para registrar una biblioteca de tipos.|  
|[CAtlComModule::UnregisterServer](../Topic/CAtlComModule::UnregisterServer.md)|Llame a este método para anular el registro de cada objeto del mapa del objeto.|  
|[CAtlComModule::UnRegisterTypeLib](../Topic/CAtlComModule::UnRegisterTypeLib.md)|Llame a este método anular el registro de una biblioteca de tipos.|  
  
## Comentarios  
 `CAtlComModule` implementa un módulo de servidor COM, lo que un cliente tiene acceso a los componentes de módulo.  
  
 Esta clase reemplaza la clase obsoletos de [CComModule](../../atl/reference/ccommodule-class.md) utilizada en versiones anteriores de ATL.  Vea [Clases de módulo ATL](../../atl/atl-module-classes.md) para más detalles.  
  
## Jerarquía de herencia  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)  
  
 `CAtlComModule`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [\_ATL\_COM\_MODULE](../Topic/_ATL_COM_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)