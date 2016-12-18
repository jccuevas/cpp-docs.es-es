---
title: "Using IDispEventSimpleImpl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDispEventSimpleImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventSimpleImpl class, utilizar"
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using IDispEventSimpleImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al utilizar `IDispEventSimpleImpl` para controlar eventos, necesitará:  
  
-   derive la clase de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).  
  
-   agregue [mapa de receptor de eventos](../Topic/BEGIN_SINK_MAP.md) a la clase.  
  
-   defina las estructuras de [\_ATL\_FUNC\_INFORMATION](../atl/reference/atl-func-info-structure.md) que describen los eventos.  
  
-   Agregue las entradas al receptor de eventos asignado mediante la macro de [SINK\_ENTRY\_INFORMATION](../Topic/SINK_ENTRY_INFO.md) .  
  
-   Implemente los métodos que está interesado en administrar.  
  
-   Advise y unadvise el origen de eventos.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo controlar el evento de **DocumentChange** desencadenado por el objeto de **Aplicación** de word.  Este evento se define como un método en el dispinterface de **ApplicationEvents** .  
  
 el ejemplo es de [Ejemplo ATLEventHandling](../top/visual-cpp-samples.md).  
  
 `[`  
  
 `uuid(000209F7-0000-0000-C000-000000000046),`  
  
 `hidden`  
  
 `]`  
  
 `dispinterface ApplicationEvents {`  
  
 `properties:`  
  
 `methods:`  
  
 `[id(0x00000001), restricted, hidden]`  
  
 `void Startup();`  
  
 `[id(0x00000002)]`  
  
 `void Quit();`  
  
 `[id(0x00000003)]`  
  
 `void DocumentChange();`  
  
 `};`  
  
 El ejemplo utiliza `#import` para generar los archivos de encabezado necesarios de la biblioteca de tipos de word.  Si desea utilizar este ejemplo con otras versiones de word, debe especificar el archivo correcto DLL mso.  Por ejemplo, Office 2000 proporciona mso9.dll y Office XP proporciona mso.dll.  Este código se simplifica stdafx.h:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventsimpleimpl_1.h)]  
  
 La única información de la biblioteca de tipos utilizada realmente en este ejemplo es el CLSID del objeto de **Aplicación** de word y el IID de la interfaz de **ApplicationEvents** .  Esta información se utiliza en tiempo de compilación.  
  
 el código siguiente aparece en Simple.h.  El código pertinente es anotado por comentarios:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/CPP/using-idispeventsimpleimpl_2.h)]  
  
 el código siguiente es de Simple.cpp:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/CPP/using-idispeventsimpleimpl_3.cpp)]  
  
## Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)   
 [Ejemplo ATLEventHandling](../top/visual-cpp-samples.md)