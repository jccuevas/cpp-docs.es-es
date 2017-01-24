---
title: "Using IDispEventImpl | Microsoft Docs"
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
  - "IDispEventImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDispEventImpl class, utilizar"
ms.assetid: 82d53b61-9d0d-45c5-aff9-2fafa468a9ca
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using IDispEventImpl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al utilizar `IDispEventImpl` para controlar eventos, necesitará:  
  
-   derive la clase de [IDispEventImpl](../atl/reference/idispeventimpl-class.md).  
  
-   agregue [mapa de receptor de eventos](../Topic/BEGIN_SINK_MAP.md) a la clase.  
  
-   Agregue las entradas al receptor de eventos asignado mediante la macro de [SINK\_ENTRY](../Topic/SINK_ENTRY.md) o de [SINK\_ENTRY\_EX](../Topic/SINK_ENTRY_EX.md) .  
  
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
  
 [!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/CPP/using-idispeventimpl_1.h)]  
  
 el código siguiente aparece en NotSoSimple.h.  El código pertinente es anotado por comentarios:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample#2](../atl/codesnippet/CPP/using-idispeventimpl_2.h)]  
  
## Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)   
 [Ejemplo ATLEventHandling](../top/visual-cpp-samples.md)