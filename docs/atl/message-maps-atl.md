---
title: (ATL) de mapas de mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message maps, ATL
- ATL, message handlers
ms.assetid: 9e100400-65c7-4a85-8857-4e6cb6dd7340
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 650dcd31e07ef1995f09b0521991d79726b22774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="message-maps-atl"></a>Mapas de mensajes (ATL)
Un mapa de mensajes asocia una función de controlador con un mensaje determinado, un comando o una notificación. Mediante el uso de ATL [macros de mapa de mensajes](../atl/reference/message-map-macros-atl.md), puede especificar un mapa de mensajes de una ventana. Los procedimientos de ventana de `CWindowImpl`, `CDialogImpl`, y `CContainedWindowT` dirigir los mensajes de una ventana a su mapa de mensajes.  
  
 El [las funciones de controlador de mensaje](../atl/message-handler-functions.md) aceptan un argumento adicional de tipo `BOOL&`. Este argumento indica si se ha procesado un mensaje, y se establece en `TRUE` de forma predeterminada. Una función de controlador, a continuación, puede establecer el argumento en `FALSE` para indicar que no ha controlado un mensaje. En este caso, ATL continuará buscando una función controladora más adelante en el mapa de mensajes. Si establece este argumento en `FALSE`, puede realizar alguna acción en respuesta a un mensaje y, a continuación, permitir el procesamiento predeterminado u otra función de controlador para terminar de controlar el mensaje.  
  
## <a name="chained-message-maps"></a>Mapas de mensajes encadenados  
 ATL también permite encadenar mapas de mensajes, que dirige el control a un mapa de mensajes definido en otra clase de mensajes. Por ejemplo, puede implementar el control de mensajes común en una clase independiente para proporcionar un comportamiento uniforme para todas las ventanas encadenadas a esa clase. Puede encadenar a una clase base o a un miembro de datos de la clase.  
  
 ATL también admite el encadenamiento dinámico, lo que permite encadenar a mapa de mensajes de otro objeto en tiempo de ejecución. Para implementar un encadenamiento dinámico, debe derivar la clase de [CDynamicChain](../atl/reference/cdynamicchain-class.md). A continuación, declare la [CHAIN_MSG_MAP_DYNAMIC](reference/message-map-macros-atl.md#chain_msg_map_dynamic) macro en el mapa de mensajes. `CHAIN_MSG_MAP_DYNAMIC`requiere un número único que identifica el objeto y el mapa de mensajes a la que está encadenando. Debe definir este valor único mediante una llamada a `CDynamicChain::SetChainEntry`.  
  
 Puede encadenar a cualquier clase que declara un mapa de mensajes, siempre que la clase se deriva de [CMessageMap](../atl/reference/cmessagemap-class.md). `CMessageMap`permite que un objeto exponer sus mapas de mensajes a otros objetos. Tenga en cuenta que `CWindowImpl` ya se deriva de `CMessageMap`.  
  
## <a name="alternate-message-maps"></a>Mapas de mensajes alternativos  
 Por último, ATL es compatible con los mapas de mensajes alternativo, declarados con la [ALT_MSG_MAP](reference/message-map-macros-atl.md#alt_msg_map) macro. Cada mapa de mensajes alternativo se identifica mediante un número único, que se pasa a `ALT_MSG_MAP`. Uso de mensajes alternativo se asigna, puede controlar los mensajes de varias ventanas en una asignación. Tenga en cuenta que de forma predeterminada, `CWindowImpl` no utiliza mapas de mensajes alternativos. Para agregar esta compatibilidad, invalide el `WindowProc` método en su `CWindowImpl`-derivado de la clase y llame al método `ProcessWindowMessage` con el identificador del mapa de mensajes.  
  
## <a name="see-also"></a>Vea también  
 [Implementar una ventana](../atl/implementing-a-window.md)

