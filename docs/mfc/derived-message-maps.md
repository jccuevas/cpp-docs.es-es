---
title: Derivado de mapas de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e780d411e62d1347d8286f86b45df864b0fcdb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342971"
---
# <a name="derived-message-maps"></a>Mapas de mensajes derivados
Durante el control de mensajes, la comprobación de un mensaje de la clase map no es el final de la historia de mapa de mensajes. ¿Qué ocurre si clase `CMyView` (derivado de `CView`) no tiene ninguna entrada coincidente para un mensaje  
  
 Tenga en cuenta que `CView`, la clase base de `CMyView`, se deriva a su vez `CWnd`. Por lo tanto `CMyView` *es* una `CView` y *es* un `CWnd`. Cada una de esas clases tiene su propio mapa de mensajes. En la ilustración "Una jerarquía de vistas" a continuación se muestra la relación jerárquica de las clases, pero tenga en cuenta que un `CMyView` objeto es un objeto único que tiene las características de las tres clases.  
  
 ![Jerarquía de una vista](../mfc/media/vc38621.gif "vc38621")  
Una jerarquía de vistas  
  
 Por tanto, si no se puede asociar un mensaje en la clase `CMyView`del mapa de mensajes, el marco de trabajo también busca en el mapa de mensajes de su clase base inmediata. El `BEGIN_MESSAGE_MAP` macro al principio del mapa de mensajes especifica dos nombres de clase como argumentos:  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]  
  
 El primer argumento de nombre a la clase a la que pertenece el mapa de mensajes. El segundo argumento proporciona una conexión con la clase base inmediata: `CView` aquí: para que el marco de trabajo puedan buscar su mapa de mensajes, demasiado.  
  
 La clase derivada, por tanto, heredan los controladores de mensajes que se proporciona en una clase base. Esto es muy similar a las funciones miembro virtuales normales sin necesidad de realizar todas las funciones de miembro de controlador virtual.  
  
 Si no hay ningún controlador se encuentra en cualquiera de los mapas de mensajes de la clase base, se realiza el procesamiento predeterminado del mensaje. Si el mensaje es un comando, el marco de trabajo lo enruta al destino de comando siguiente. Si es un mensaje de Windows estándar, el mensaje se pasa al procedimiento de ventana predeterminado adecuado.  
  
 Para acelerar la búsqueda de coincidencias de mapa de mensajes, el marco de trabajo almacena en caché a recientes coincidencias en la probabilidad de que recibirá el mismo mensaje de nuevo. Una consecuencia de esto es que el marco de trabajo procesa los mensajes no controlados bastante eficaz. Mapas de mensajes son también más espacio-eficaces que las implementaciones que usan funciones virtuales.  
  
## <a name="see-also"></a>Vea también  
 [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)

