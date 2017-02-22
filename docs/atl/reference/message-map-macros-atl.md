---
title: "Message Map Macros (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: eefdd546-8934-4a30-b263-9c06a8addcbd
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Message Map Macros (ATL)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas macros definen mapas y entradas del mensaje.  
  
|||  
|-|-|  
|[ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)|Marca el principio de un mapa de mensajes alternativo.|  
|[BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)|Marca el principio del mapa de mensajes predeterminado.|  
|[CHAIN\_MSG\_MAP\_ALT](../Topic/CHAIN_MSG_MAP_ALT.md)|cadenas a un mensaje alternativo asignado en la clase base.|  
|[CHAIN\_MSG\_MAP\_ALT\_MEMBER](../Topic/CHAIN_MSG_MAP_ALT_MEMBER.md)|cadenas a un mensaje alternativo asignado en un miembro de datos de la clase.|  
|[CHAIN\_MSG\_MAP](../Topic/CHAIN_MSG_MAP.md)|Cadenas al mensaje predeterminado asignado en la clase base.|  
|[CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md)|Cadenas al mensaje asignado en otra clase en tiempo de ejecución.|  
|[CHAIN\_MSG\_MAP\_MEMBER](../Topic/CHAIN_MSG_MAP_MEMBER.md)|Cadenas al mensaje predeterminado asignado en un miembro de datos de la clase.|  
|[COMMAND\_CODE\_HANDLER](../Topic/COMMAND_CODE_HANDLER.md)|Asigna un mensaje de **WM\_COMMAND** a una función controladora, basándose en el código de notificación.|  
|[COMMAND\_HANDLER](../Topic/COMMAND_HANDLER.md)|Asigna un mensaje de **WM\_COMMAND** a una función controladora, basándose en el código de notificación y el identificador del elemento de menú, del control, o de aceleradores.|  
|[COMMAND\_ID\_HANDLER](../Topic/COMMAND_ID_HANDLER.md)|Asigna un mensaje de **WM\_COMMAND** a una función controladora, según el identificador del elemento de menú, del control, o de aceleradores.|  
|[COMMAND\_RANGE\_CODE\_HANDLER](../Topic/COMMAND_RANGE_CODE_HANDLER.md)|Asigna un mensaje de **WM\_COMMAND** a una función controladora, basándose en el código de notificación y un intervalo contiguo de identificadores de control.|  
|[COMMAND\_RANGE\_HANDLER](../Topic/COMMAND_RANGE_HANDLER.md)|Asigna un mensaje de **WM\_COMMAND** a una función controladora, basándose en un intervalo contiguo de identificadores de control.|  
|[DECLARE\_EMPTY\_MSG\_MAP](../Topic/DECLARE_EMPTY_MSG_MAP.md)|Implementa un mapa de mensajes vacío.|  
|[DEFAULT\_REFLECTION\_HANDLER](../Topic/DEFAULT_REFLECTION_HANDLER.md)|Proporciona un controlador predeterminado para los mensajes reflejados que no se controlan de otra manera.|  
|[END\_MSG\_MAP](../Topic/END_MSG_MAP.md)|Marca el final de un mapa de mensajes.|  
|[FORWARD\_NOTIFICATIONS](../Topic/FORWARD_NOTIFICATIONS.md)|transmite a mensajes de notificación la ventana primaria.|  
|[MESSAGE\_HANDLER](../Topic/MESSAGE_HANDLER.md)|Asigna un mensaje de Windows a una función de controlador.|  
|[MESSAGE\_RANGE\_HANDLER](../Topic/MESSAGE_RANGE_HANDLER.md)|Asigna un intervalo contiguo de los mensajes de Windows a una función de controlador.|  
|[NOTIFY\_CODE\_HANDLER](../Topic/NOTIFY_CODE_HANDLER.md)|Asigna un mensaje de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación.|  
|[NOTIFY\_HANDLER](../Topic/NOTIFY_HANDLER.md)|Asigna un mensaje de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación y el identificador de control.|  
|[NOTIFY\_ID\_HANDLER](../Topic/NOTIFY_ID_HANDLER.md)|Asigna un mensaje de **WM\_NOTIFY** a una función controladora, según el identificador de control.|  
|[NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/NOTIFY_RANGE_CODE_HANDLER.md)|Asigna un mensaje de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación y un intervalo contiguo de identificadores de control.|  
|[NOTIFY\_RANGE\_HANDLER](../Topic/NOTIFY_RANGE_HANDLER.md)|Asigna un mensaje de **WM\_NOTIFY** a una función controladora, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECT\_NOTIFICATIONS](../Topic/REFLECT_NOTIFICATIONS.md)|Refleja mensajes de notificación a la ventana que los envió.|  
|[REFLECTED\_COMMAND\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_CODE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_COMMAND** a una función controladora, basándose en el código de notificación.|  
|[REFLECTED\_COMMAND\_HANDLER](../Topic/REFLECTED_COMMAND_HANDLER.md)|Asigna un mensaje reflejado de **WM\_COMMAND** a una función controladora, basándose en el código de notificación y el identificador del elemento de menú, del control, o de aceleradores.|  
|[REFLECTED\_COMMAND\_ID\_HANDLER](../Topic/REFLECTED_COMMAND_ID_HANDLER.md)|Asigna un mensaje reflejado de **WM\_COMMAND** a una función controladora, según el identificador del elemento de menú, del control, o de aceleradores.|  
|[REFLECTED\_COMMAND\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_CODE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_COMMAND** a una función controladora, basándose en el código de notificación y un intervalo contiguo de identificadores de control.|  
|[REFLECTED\_COMMAND\_RANGE\_HANDLER](../Topic/REFLECTED_COMMAND_RANGE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_COMMAND** a una función controladora, basándose en un intervalo contiguo de identificadores de control.|  
|[REFLECTED\_NOTIFY\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_CODE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación.|  
|[REFLECTED\_NOTIFY\_HANDLER](../Topic/REFLECTED_NOTIFY_HANDLER.md)|Asigna un mensaje reflejado de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación y el identificador de control.|  
|[REFLECTED\_NOTIFY\_ID\_HANDLER](../Topic/REFLECTED_NOTIFY_ID_HANDLER.md)|Asigna un mensaje reflejado de **WM\_NOTIFY** a una función controladora, según el identificador de control.|  
|[REFLECTED\_NOTIFY\_RANGE\_CODE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_CODE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_NOTIFY** a una función controladora, basándose en el código de notificación y un intervalo contiguo de identificadores de control.|  
|[REFLECTED\_NOTIFY\_RANGE\_HANDLER](../Topic/REFLECTED_NOTIFY_RANGE_HANDLER.md)|Asigna un mensaje reflejado de **WM\_NOTIFY** a una función controladora, basándose en un intervalo contiguo de identificadores de control.|  
  
## Vea también  
 [Macros](../../atl/reference/atl-macros.md)