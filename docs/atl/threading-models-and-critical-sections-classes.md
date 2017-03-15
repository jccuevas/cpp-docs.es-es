---
title: "Threading Models and Critical Sections Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.threads.models"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, critical sections"
  - "ATL, multithreading"
  - "critical sections"
  - "subprocesamiento [ATL], modelos"
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Threading Models and Critical Sections Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

las clases siguientes definen un modelo de subprocesos y una sección crítica:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementa subproceso\- haber agrupado, servidor COM de apartamento\- modelo.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) proporciona métodos para implementar subproceso\- haber agrupado, servidor COM de apartamento\- modelo.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) proporciona métodos seguros para subprocesos para aumentar y disminuir una variable.  proporciona una sección crítica.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) proporciona métodos seguros para subprocesos para aumentar y disminuir una variable.  no proporciona una sección crítica.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) proporciona métodos para aumentar y disminuir una variable.  no proporciona una sección crítica.  
  
-   [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) determina la clase correspondiente del modelo de subprocesos para una única clase de objeto.  
  
-   [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) determina la clase correspondiente del modelo de subprocesos de un objeto que es global disponible.  
  
-   Métodos de[CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) Contains para obtener y liberar una sección crítica.  la sección crítica automáticamente se inicializa.  
  
-   Métodos de[CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) Contains para obtener y liberar una sección crítica.  La sección crítica debe inicializar explícitamente.  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) refleja los métodos en `CComCriticalSection` sin proporcionar una sección crítica.  Los métodos de `CComFakeCriticalSection` no hacen nada.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) proporciona la función de creación para un subproceso de CRT.  Utilice esta clase si el subproceso utiliza funciones de CRT.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) proporciona la función de creación para un subproceso de Windows.  Utilice esta clase si el subproceso no utiliza funciones de CRT.  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)