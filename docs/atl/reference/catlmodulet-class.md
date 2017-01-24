---
title: "CAtlModuleT Class | Microsoft Docs"
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
  - "ATL::CAtlModuleT<T>"
  - "ATL.CAtlModuleT"
  - "ATL.CAtlModuleT<T>"
  - "ATL::CAtlModuleT"
  - "CAtlModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModuleT class"
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa un módulo de ATL.  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>   
class ATL_NO_VTABLE CAtlModuleT :  
   public CAtlModule  
```  
  
#### Parámetros  
 `T`  
 la clase derivada de `CAtlModuleT`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](../Topic/CAtlModuleT::CAtlModuleT.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](../Topic/CAtlModuleT::InitLibId.md)|Inicializa el miembro de datos que contiene el GUID del módulo actual.|  
|[CAtlModuleT::RegisterAppId](../Topic/CAtlModuleT::RegisterAppId.md)|Agrega un archivo EXE en el registro.|  
|[CAtlModuleT::RegisterServer](../Topic/CAtlModuleT::RegisterServer.md)|Agrega el servicio al registro.|  
|[CAtlModuleT::UnregisterAppId](../Topic/CAtlModuleT::UnregisterAppId.md)|Quita un archivo EXE del registro.|  
|[CAtlModuleT::UnregisterServer](../Topic/CAtlModuleT::UnregisterServer.md)|Quita el servicio de registro.|  
|[CAtlModuleT::UpdateRegistryAppId](../Topic/CAtlModuleT::UpdateRegistryAppId.md)|Actualiza la información del archivo EXE en el registro.|  
  
## Comentarios  
 `CAtlModuleT`, derivado de [CAtlModule](../../atl/reference/catlmodule-class.md), implementa una aplicación ejecutable \(EXE\) o un módulo de Service \(EXE\) ATL.  Un módulo ejecutable es un valor local, servidor fuera de proceso, mientras que un módulo de Servicio es una aplicación para Windows que se ejecuta en segundo plano cuando se inicie Windows.  
  
 `CAtlModuleT` proporciona compatibilidad para inicializar, registrar, y la anulación del módulo.  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CAtlModule Class](../../atl/reference/catlmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)