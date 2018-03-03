---
title: "Clases de las secciones críticas (ATL) y modelos de subprocesos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1501fe4f761b9bc8775018d6566ceff5fb0aa477
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="threading-models-and-critical-sections-classes"></a>Los modelos y las clases de las secciones críticas de subprocesos
Las clases siguientes definen un subprocesamiento modelo y sección crítica:  
  
-   [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementa un servidor COM agrupadas por subproceso, el modelo de apartamento.  
  
-   [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) ofrece métodos para implementar un servidor COM agrupadas por subproceso, el modelo de apartamento.  
  
-   [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) proporciona métodos de subprocesos para aumentar y disminuir una variable. Proporciona una sección crítica.  
  
-   [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) proporciona métodos de subprocesos para aumentar y disminuir una variable. No se proporciona una sección crítica.  
  
-   [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) proporciona métodos para aumentar y disminuir una variable. No se proporciona una sección crítica.  
  
-   [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) determina la clase de modelo de subprocesamiento adecuada para una clase de objeto único.  
  
-   [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) determina la clase de modelo de subprocesamiento adecuada para un objeto que está disponible globalmente.  
  
-   [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) contiene métodos para la obtención y liberación de una sección crítica. La sección crítica se inicializa automáticamente.  
  
-   [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) contiene métodos para la obtención y liberación de una sección crítica. La sección crítica debe inicializarse explícitamente.  
  
-   [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) refleja los métodos de `CComCriticalSection` sin proporcionar una sección crítica. Los métodos de `CComFakeCriticalSection` no hacen nada.  
  
-   [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) proporciona la función de creación de un subproceso de CRT. Utilice esta clase si el subproceso usará las funciones de CRT.  
  
-   [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) proporciona la función de creación de un subproceso de Windows. Utilice esta clase si el subproceso no utiliza funciones de CRT.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)

