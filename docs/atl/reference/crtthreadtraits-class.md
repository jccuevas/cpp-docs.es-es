---
title: "CRTThreadTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CRTThreadTraits"
  - "ATL.CRTThreadTraits"
  - "CRTThreadTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRTThreadTraits class"
  - "subprocesamiento [ATL], creation functions"
  - "subprocesamiento [ATL], CRT threads"
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CRTThreadTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona la función de creación para un subproceso de CRT.  Utilice esta clase si el subproceso utiliza funciones de CRT.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CRTThreadTraits  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRTThreadTraits::CreateThread](../Topic/CRTThreadTraits::CreateThread.md)|\(Estático\) llame a esta función para crear un subproceso que pueda usar las funciones CRT.|  
  
## Comentarios  
 Los rasgos de subprocesos son clases que proporcionan una función de creación para un tipo determinado de subproceso.  La función de creación tienen la misma firma y semántica que la función de Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) .  
  
 Los rasgos de subproceso usan las clases siguientes:  
  
-   [CThreadPool](../../atl/reference/cthreadpool-class.md)  
  
-   [CWorkerThread](../../atl/reference/cworkerthread-class.md)  
  
 Si el subproceso no utiliza funciones de CRT, utilice [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) en su lugar.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)