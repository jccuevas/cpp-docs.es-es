---
title: "Mapas de receptor de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de receptor de eventos"
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Mapas de receptor de eventos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando un control OLE incrustado desencadena un evento, el contenedor del control recibe el evento utilizando un mecanismo, denominado “mapa de receptor de eventos,” proporcionada por MFC.  Este mapa de receptor de eventos señala las funciones controladoras para cada evento concreto, así como los parámetros de esos eventos.  Para obtener más información sobre asignaciones de receptor de eventos, vea el artículo [Contenedores de controles ActiveX](../../mfc/activex-control-containers.md).  
  
### Mapas de receptor de eventos  
  
|||  
|-|-|  
|[BEGIN\_EVENTSINK\_MAP](../Topic/BEGIN_EVENTSINK_MAP.md)|Inicia la definición de un mapa de receptor de eventos.|  
|[DECLARE\_EVENTSINK\_MAP](../Topic/DECLARE_EVENTSINK_MAP.md)|Declara un mapa de receptor de eventos.|  
|[END\_EVENTSINK\_MAP](../Topic/END_EVENTSINK_MAP.md)|Finaliza la definición de un mapa de receptor de eventos.|  
|[ON\_EVENT](../Topic/ON_EVENT.md)|Define un controlador de eventos para un evento específico.|  
|[ON\_EVENT\_RANGE](../Topic/ON_EVENT_RANGE.md)|Define un controlador de eventos para un evento específico desencadenado de un conjunto de controles OLE.|  
|[ON\_EVENT\_REFLECT](../Topic/ON_EVENT_REFLECT.md)|Recibe los eventos desencadenados por el control antes de que se administran mediante el contenedor del control.|  
|[ON\_PROPNOTIFY](../Topic/ON_PROPNOTIFY.md)|Define un controlador para administrar notificaciones de la propiedad de un control OLE.|  
|[ON\_PROPNOTIFY\_RANGE](../Topic/ON_PROPNOTIFY_RANGE.md)|Define un controlador para administrar notificaciones de la propiedad de un conjunto de controles OLE.|  
|[ON\_PROPNOTIFY\_REFLECT](../Topic/ON_PROPNOTIFY_REFLECT.md)|Recibe las notificaciones de la propiedad enviada por el control antes de que se administran mediante el contenedor del control.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)