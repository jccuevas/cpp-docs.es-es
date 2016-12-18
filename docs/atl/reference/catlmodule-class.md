---
title: "CAtlModule Class | Microsoft Docs"
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
  - "ATL::CAtlModule"
  - "CAtlModule"
  - "ATL.CAtlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModule class"
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona los métodos que usa varias clases de módulo ATL.  
  
## Sintaxis  
  
```  
  
   class ATL_NO_VTABLE CAtlModule :  
public _ATL_MODULE  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](../Topic/CAtlModule::CAtlModule.md)|el constructor.|  
|[CAtlModule::~CAtlModule](../Topic/CAtlModule::~CAtlModule.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](../Topic/CAtlModule::AddCommonRGSReplacements.md)|Invalide este método para agregar parámetros al mapa componente de reemplazo de registro ATL \(registro\).|  
|[CAtlModule::AddTermFunc](../Topic/CAtlModule::AddTermFunc.md)|Agrega una nueva función que se va a llamar cuando el módulo finaliza.|  
|[CAtlModule::GetGITPtr](../Topic/CAtlModule::GetGITPtr.md)|Devuelve el puntero de interfaz de Global.|  
|[CAtlModule::GetLockCount](../Topic/CAtlModule::GetLockCount.md)|Devuelve el recuento de bloqueo.|  
|[CAtlModule::Lock](../Topic/CAtlModule::Lock.md)|Incrementa el recuento de bloqueo.|  
|[CAtlModule::Term](../Topic/CAtlModule::Term.md)|Libera todos los miembros de datos.|  
|[CAtlModule::Unlock](../Topic/CAtlModule::Unlock.md)|Reduce el recuento de bloqueos.|  
|[CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md)|Ejecute el script contenido en el recurso especificado al que se utiliza con un objeto.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](../Topic/CAtlModule::UpdateRegistryFromResourceDHelper.md)|Este método llama `UpdateRegistryFromResourceD` para realizar la actualización del registro.|  
|[CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md)|Ejecute el script contenido en el recurso especificado al que se utiliza con un objeto.  Vínculos de este método estáticamente el componente de registro ATL.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModule::m\_libid](../Topic/CAtlModule::m_libid.md)|Contiene el GUID del módulo actual.|  
|[CAtlModule::m\_pGIT](../Topic/CAtlModule::m_pGIT.md)|puntero a la tabla de la interfaz de Global.|  
  
## Comentarios  
 Esta clase es utilizada por [clase de CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md), [clase de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md), y [clase de CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) para proporcionar compatibilidad con aplicaciones de DLL, las aplicaciones EXE, y los servicios de Windows, respectivamente.  
  
 Para obtener más información sobre los módulos de ATL, vea [Clases de módulo ATL](../../atl/atl-module-classes.md).  
  
 esta clase reemplaza [clase de CComModule](../../atl/reference/ccommodule-class.md) obsoleto utilizado en versiones anteriores de ATL.  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 `CAtlModule`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)   
 [Componente de registro \(Registrador\)](../../atl/atl-registry-component-registrar.md)