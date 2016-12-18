---
title: "Mapas de conexiones | Microsoft Docs"
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
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de conexiones"
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de conexiones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controles OLE pueden exponer interfaces a otras aplicaciones.  Estas interfaces permiten sólo acceso de un contenedor de ese control.  Si un control OLE desea tener acceso a las interfaces externas de otros objetos OLE, un punto de conexión establecido.  Este pin ofrece al control el acceso de salida a los mapas externos de envío, como mapas de eventos o notificación funciona.  
  
 La biblioteca MFC \(Microsoft Foundation Class\) proporciona un modelo de programación que admita los puntos de conexión.  En este modelo, “asigna la conexión” se utilizan para señalar interfaces o puntos de conexión para el control OLE.  Los mapas de la conexión contienen una macro para cada punto de conexión.  Para obtener más información sobre asignaciones de conexión, vea la clase de [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) .  
  
 Normalmente, un control admitirá sólo dos puntos de conexión: uno de los eventos y otro para las notificaciones de cambio de propiedad.  Éstos son implementados por la clase base de `COleControl` y no requieren ningún trabajo adicional del programador del control.  Puntos de conexión adicional que desee implementar en la clase debe agregar manualmente.  Para admitir mapas y los puntos de conexión, MFC proporciona las siguientes macros:  
  
### Declaración y Demarcation de mapa de la conexión  
  
|||  
|-|-|  
|[BEGIN\_CONNECTION\_PART](../Topic/BEGIN_CONNECTION_PART.md)|Declara una clase incrustada que implementa un punto de conexión adicional \(se utiliza en la declaración de clase\).|  
|[END\_CONNECTION\_PART](../Topic/END_CONNECTION_PART.md)|Finaliza la declaración de un punto de conexión \(se utiliza en la declaración de clase\).|  
|[CONNECTION\_IID](../Topic/CONNECTION_IID.md)|Especifica el identificador de la interfaz de punto de conexión del control.|  
|[DECLARE\_CONNECTION\_MAP](../Topic/DECLARE_CONNECTION_MAP.md)|Declara que un mapa de conexión se utiliza en una clase \(se utiliza en la declaración de clase\).|  
|[BEGIN\_CONNECTION\_MAP](../Topic/BEGIN_CONNECTION_MAP.md)|Inicia la definición de un mapa de conexión \(se utiliza en la implementación de la clase\).|  
|[END\_CONNECTION\_MAP](../Topic/END_CONNECTION_MAP.md)|Finaliza la definición de un mapa de conexión \(se utiliza en la implementación de la clase\).|  
|[CONNECTION\_PART](../Topic/CONNECTION_PART.md)|Especifica un punto de conexión en la asignación de la conexión del control.|  
  
 Las siguientes funciones ayudan a un receptor en el establecimiento y la desconexión de una conexión de puntos de conexión:  
  
### Inicialización o finalización de puntos de conexión  
  
|||  
|-|-|  
|[AfxConnectionAdvise](../Topic/AfxConnectionAdvise.md)|Establece una conexión entre un origen y un receptor.|  
|[AfxConnectionUnadvise](../Topic/AfxConnectionUnadvise.md)|Interrumpe una conexión entre un origen y un receptor.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)