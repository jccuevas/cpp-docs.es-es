---
title: "CComAutoThreadModule Class | Microsoft Docs"
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
  - "CComAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartment model modules"
  - "CComAutoThreadModule class"
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

A partir de ATL 7,0, `CComAutoThreadModule` está obsoleto: vea [Clases de módulo ATL](../../atl/atl-module-classes.md) para más detalles.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
class ThreadAllocator= CComSimpleThreadAllocator   
>  
class CComAutoThreadModule :  
public CComModule  
```  
  
#### Parámetros  
 `ThreadAllocator`  
 \[in\] tipo de El que administra la selección del subproceso.  el valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[CreateInstance](../Topic/CComAutoThreadModule::CreateInstance.md)|Selecciona un subproceso y crea un objeto en el apartamento asociado.|  
|[GetDefaultThreads](../Topic/CComAutoThreadModule::GetDefaultThreads.md)|\(Estático\) Dinámicamente calcula el número de subprocesos para el módulo según el número de procesadores.|  
|[Iniciar](../Topic/CComAutoThreadModule::Init.md)|Crea subprocesos de módulo.|  
|[Bloquear](../Topic/CComAutoThreadModule::Lock.md)|Incrementa el recuento de bloqueo del módulo y en el subproceso actual.|  
|[Unlock](../Topic/CComAutoThreadModule::Unlock.md)|Disminuye el recuento de bloqueo del módulo y en el subproceso actual.|  
  
### miembros de datos  
  
### miembros de datos  
  
|||  
|-|-|  
|[dwThreadID](../Topic/CComAutoThreadModule::dwThreadID.md)|Contiene el identificador del subproceso actual.|  
|[m\_Allocator](../Topic/CComAutoThreadModule::m_Allocator.md)|Administra la selección del subproceso.|  
|[m\_nThreads](../Topic/CComAutoThreadModule::m_nThreads.md)|Contiene el número de subprocesos del módulo.|  
|[m\_pApartments](../Topic/CComAutoThreadModule::m_pApartments.md)|Administra los apartamentos de módulo.|  
  
## Comentarios  
  
> [!NOTE]
>  Esta clase está obsoleta, ser reemplazado por las clases derivadas de [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) y de [CAtlModule](../../atl/reference/catlmodule-class.md) .  La información que sigue es para uso con anteriores versiones ATL.  
  
 `CComAutoThreadModule` deriva de [CComModule](../../atl/reference/ccommodule-class.md) para implementar un servidor COM subproceso\- reunida, de apartamento\- modelo para EXE y servicios de Windows.  `CComAutoThreadModule` utiliza [CComApartment](../../atl/reference/ccomapartment-class.md) para administrar un apartamento para cada subproceso del módulo.  
  
 Derive el módulo de `CComAutoThreadModule` cuando desee crear objetos en apartamentos múltiples.  También debe incluir la macro de [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) en la definición de clase del objeto para especificar [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) como el generador de la clase.  
  
 De forma predeterminada, el AppWizard ATL COM \(el asistente para proyectos ATL en Visual Studio .NET\) derivará el módulo de `CComModule`.  Para utilizar `CComAutoThreadModule`, modifique la definición de clase.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/CPP/ccomautothreadmodule-class_1.cpp)]  
  
## Jerarquía de herencia  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)