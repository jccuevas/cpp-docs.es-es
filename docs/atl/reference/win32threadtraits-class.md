---
title: "Win32ThreadTraits Class | Microsoft Docs"
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
  - "Win32ThreadTraits"
  - "ATL::Win32ThreadTraits"
  - "ATL.Win32ThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subprocesamiento [ATL], creation functions"
  - "subprocesamiento [ATL], Windows threads"
  - "Win32ThreadTraits class"
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Win32ThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona la función de creación para un subproceso de Windows.  Utilice esta clase si el subproceso no utiliza funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class Win32ThreadTraits  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Win32ThreadTraits::CreateThread](../Topic/Win32ThreadTraits::CreateThread.md)|\(Estático\) llame a esta función para crear un subproceso que no utilicen funciones CRT.|  
  
## Comentarios  
 Los rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso.  La función de creación tienen la misma firma y semántica que la función de Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) .  
  
 Los rasgos de subproceso usan las clases siguientes:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso utiliza funciones de CRT, utilice [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) en su lugar.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)