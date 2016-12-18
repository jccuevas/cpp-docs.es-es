---
title: "Mapas de eventos | Microsoft Docs"
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
  - "mapas de eventos"
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de eventos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Siempre que deseos de un control para notificar el contenedor que se ha producido alguna acción \(determinado por el programador de controles\) \(por ejemplo una tecla; clic del mouse, o un cambio en el estado de control\) se llama una función de la evento\- desencadenamiento.  Esta función notifica al contenedor del control que alguna acción importante ha producido desencadena el evento relacionado.  
  
 La biblioteca MFC \(Microsoft Foundation Class\) proporciona un modelo de programación optimizado para desencadenar eventos.  En este modelo, “los mapas del evento” se utilizan para indicar que el activación que los eventos de un control determinado.  Los mapas del evento contienen una macro para cada evento.  Por ejemplo, un evento asigna que desencadena un evento Click común sería similar a:  
  
 [!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/CPP/event-maps_1.cpp)]  
  
 La macro de **EVENT\_STOCK\_CLICK** indica que el control producirá un evento Click común que detecta cada vez un clic del mouse.  Para obtener una lista más detallada de otros eventos comunes, vea el artículo [Controles ActiveX: Eventos](../../mfc/mfc-activex-controls-events.md).  Las macros también están disponibles indicar eventos personalizados.  
  
 Aunque macros de evento\- mapa son importantes, no las inserta normalmente directamente.  Esto se debe a que la ventana Propiedades automáticamente crea entradas de evento\- mapa en los archivos de código fuente cuando se utiliza para asociar las funciones de evento\- despedida con eventos.  Siempre que desea editar o para agregar una entrada de evento\- mapa, puede utilizar la ventana Propiedades.  
  
 Para admitir mapas de evento, MFC proporciona las siguientes macros:  
  
### Declaración y Demarcation de mapa de eventos  
  
|||  
|-|-|  
|[DECLARE\_EVENT\_MAP](../Topic/DECLARE_EVENT_MAP.md)|Declara que un mapa de eventos se utilizará en una clase para asignar los eventos a las funciones de la evento\- despedida \(se utiliza en la declaración de clase\).|  
|[BEGIN\_EVENT\_MAP](../Topic/BEGIN_EVENT_MAP.md)|Inicia la definición de un mapa de eventos \(se utiliza en la implementación de la clase\).|  
|[END\_EVENT\_MAP](../Topic/END_EVENT_MAP.md)|Finaliza la definición de un mapa de eventos \(se utiliza en la implementación de la clase\).|  
  
### Macros de asignación de eventos  
  
|||  
|-|-|  
|[EVENT\_CUSTOM](../Topic/EVENT_CUSTOM.md)|Indica qué función de la evento\-despedida desencadenará el evento especificado.|  
|[EVENT\_CUSTOM\_ID](../Topic/EVENT_CUSTOM_ID.md)|Indica qué función de la evento\- despedida desencadenará el evento especificado, con un identificador designada de envío|  
  
### Macros de asignación de mensajes  
  
|||  
|-|-|  
|[ON\_OLEVERB](../Topic/ON_OLEVERB.md)|Indica un verbo personalizado controla el control OLE.|  
|[ON\_STDOLEVERB](../Topic/ON_STDOLEVERB.md)|Reemplaza una asignación estándar de verbo de controles activex.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)