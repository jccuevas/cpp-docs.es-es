---
title: "CAtlAutoThreadModuleT Class | Microsoft Docs"
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
  - "ATL.CAtlAutoThreadModuleT"
  - "ATL::CAtlAutoThreadModuleT"
  - "CAtlAutoThreadModuleT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModuleT class"
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlAutoThreadModuleT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para implementar subproceso\-haber agrupado, servidor COM de apartamento\-modelo.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class ThreadAllocator= CComSimpleThreadAllocator,  
DWORD dwWait= INFINITE   
>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT :  
public IAtlAutoThreadModule  
```  
  
#### Parámetros  
 `T`  
 La clase que implementa el servidor COM.  
  
 `ThreadAllocator`  
 La clase que administra la selección del subproceso.  el valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 `dwWait`  
 especifica el intervalo de tiempo de espera, en milisegundos.  El valor predeterminado es INFINITE, que significa que nunca transcurre el intervalo de tiempo de espera del método.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](../Topic/CAtlAutoThreadModuleT::GetDefaultThreads.md)|Esta función estática calcula y devuelve dinámicamente el número máximo de subprocesos para el módulo EXE, basándose en el número de procesadores.|  
  
## Comentarios  
 La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) deriva de `CAtlAutoThreadModuleT` para implementar subproceso\-haber agrupado, servidor COM de apartamento\-modelo.  reemplaza la clase obsoleto [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Esta clase no se debe usar en un archivo DLL, como el valor predeterminado de `dwWait` de INFINITE provocará un interbloqueo cuando se descarga la DLL.  
  
## Jerarquía de herencia  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)