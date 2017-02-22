---
title: "Message Maps (ATL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, controladores de mensajes"
  - "message maps, ATL"
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Message Maps (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un mapa de mensajes asocia una función controladora un mensaje determinado, a un comando, o a una notificación.  Mediante [macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md)ATL, puede especificar un mapa de mensajes para una ventana.  Los procedimientos de ventana en `CWindowImpl`, `CDialogImpl`, y `CContainedWindowT` dirigen los mensajes de una ventana al mapa de mensajes.  
  
 [funciones de controlador de mensajes](../atl/message-handler-functions.md) acepta un argumento adicional de `BOOL&`escrito.  Este argumento indica si se ha procesado un mensaje, y se establece en `TRUE` de forma predeterminada.  Una función controladora podrá establecer el argumento en `FALSE` para indicar que no ha controlado un mensaje.  En este caso, ATL continuará buscando una función controladora aún más en el mapa de mensajes.  Establecer el argumento a `FALSE`, puede primero realizar alguna acción en respuesta a un mensaje y después permitir el procesamiento predeterminado u otra función de controlador al final que administra el mensaje.  
  
## Mapas encadenados de mensajes  
 ATL también permite encadenar mapas de mensajes, que envía el control de mensajes a un definido asignado mensaje en otra clase.  Por ejemplo, puede implementar el control de mensajes común en una clase independiente para proporcionar un comportamiento uniforme para todas las ventanas que encadenan a esa clase.  Puede encadenar a una clase base o miembro de datos de la clase.  
  
 ATL también admite el encadenamiento dinámico, que permite encadenar el mensaje de otro objeto asignado en tiempo de ejecución.  Para implementar el encadenamiento dinámico, debe derivar la clase de [CDynamicChain](../atl/reference/cdynamicchain-class.md).  A continuación declare la macro de [CHAIN\_MSG\_MAP\_DYNAMIC](../Topic/CHAIN_MSG_MAP_DYNAMIC.md) en el mapa de mensajes.  `CHAIN_MSG_MAP_DYNAMIC` requiere un número único que identifica el objeto y el mensaje asignados a la que está encadenando.  Debe definir este valor único con una llamada a `CDynamicChain::SetChainEntry`.  
  
 Puede encadenar a cualquier clase que declara un mapa de mensajes, siempre que la clase derive de [CMessageMap](../atl/reference/cmessagemap-class.md).  `CMessageMap` permite a un objeto exponer los mapas de mensajes a otros objetos.  Observe que `CWindowImpl` ya se deriva de `CMessageMap`.  
  
## Mapas alternativos de mensajes  
 Finalmente, ATL admite los mapas alternativos de mensajes, declarados con la macro de [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md) .  Cada mapa de mensajes alternativo se identifica mediante un número único, que pasa a `ALT_MSG_MAP`.  Mediante mapas alternativos de mensajes, puede controlar los mensajes de varias ventanas en una asignada.  Observe que de forma predeterminada, `CWindowImpl` no los usa alternativos de mensajes.  Para agregar esta compatibilidad, invalide el método de `WindowProc` en `CWindowImpl`\- la clase derivada y llamar a `ProcessWindowMessage` con el mensaje asigna el identificador.  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)