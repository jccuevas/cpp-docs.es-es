---
title: "Macros de mapa de mensajes (MFC) | Microsoft Docs"
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
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "demarcar mensajes de Windows"
  - "macros de asignación de mensajes"
  - "rangos de asignación de mensajes"
  - "macros de asignación de mensajes"
  - "mapas de mensajes [C++], declaración y demarcación"
  - "mapas de mensajes [C++], macros"
  - "intervalos, asignación de mensajes"
  - "mensajes de Windows [C++], declaración"
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Macros de mapa de mensajes (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para admitir mapas de mensajes, MFC proporciona las siguientes macros:  
  
### Declaración de Mensaje\- mapa y macros de Demarcation  
  
|||  
|-|-|  
|[DECLARE\_MESSAGE\_MAP](../Topic/DECLARE_MESSAGE_MAP.md)|Declara que un mapa de mensajes se utiliza en una clase para asignar mensajes a funciones \(se utiliza en la declaración de clase\).|  
|[BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md)|Inicia la definición de un mapa de mensajes \(se utiliza en la implementación de la clase\).|  
|[END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md)|Finaliza la definición de un mapa de mensajes \(se utiliza en la implementación de la clase\).|  
  
### Macros de la Mensaje\-asignación  
  
|||  
|-|-|  
|[ON\_COMMAND](../Topic/ON_COMMAND.md)|Indica qué función controlará un mensaje especificado del comando.|  
|[ON\_CONTROL](../Topic/ON_CONTROL.md)|Indica qué función controlará un mensaje especificado de la CONTROL\- notificación.|  
|[ON\_MESSAGE](../Topic/ON_MESSAGE.md)|Indica qué función controlará un mensaje definido por el usuario.|  
|[ON\_OLECMD](../Topic/ON_OLECMD.md)|Indica qué función controlará un comando de menú de un DocObject o de su contenedor.|  
|[ON\_REGISTERED\_MESSAGE](../Topic/ON_REGISTERED_MESSAGE.md)|Indica qué función controlará un mensaje definido por el usuario registrado.|  
|[ON\_REGISTERED\_THREAD\_MESSAGE](../Topic/ON_REGISTERED_THREAD_MESSAGE.md)|Indica qué función controlará un mensaje definido por el usuario registrado cuando tiene una clase de `CWinThread` .|  
|[ON\_THREAD\_MESSAGE](../Topic/ON_THREAD_MESSAGE.md)|Indica qué función controlará un mensaje definido por el usuario cuando tiene una clase de `CWinThread` .|  
|[ON\_UPDATE\_COMMAND\_UI](../Topic/ON_UPDATE_COMMAND_UI.md)|Indica qué función controlará un mensaje especificado del comando de actualización de la interfaz de usuario.|  
  
### Macros de intervalo de Mensaje\- mapa  
  
|||  
|-|-|  
|[ON\_COMMAND\_RANGE](../Topic/ON_COMMAND_RANGE.md)|Indica qué función controlará el intervalo de los id. de comando especificados en los dos primeros parámetros a la macro.|  
|[ON\_UPDATE\_COMMAND\_UI\_RANGE](../Topic/ON_UPDATE_COMMAND_UI_RANGE.md)|Indica que los actualizan el controlador controlará el intervalo de los id. de comando especificados en los dos primeros parámetros a la macro.|  
|[ON\_CONTROL\_RANGE](../Topic/ON_CONTROL_RANGE.md)|Indica qué función controlará notificaciones del intervalo de los id. de control especificados en el segundo y tercer parámetros a la macro.  El primer parámetro es un mensaje de la CONTROL\- notificación, como **BN\_CLICKED**.|  
  
 Para obtener más información sobre los mapas de mensajes, macros de la declaración de mensaje\- mapa y la demarcación, y las macros de la mensaje\- asignación, vea [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md) y [Temas del control de mensajes y de asignación](../../mfc/message-handling-and-mapping.md).  Para obtener más información sobre intervalos de mensaje\- mapa, vea [Controladores para los intervalos de Mensaje\- mapa](../../mfc/handlers-for-message-map-ranges.md).  
  
## Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)