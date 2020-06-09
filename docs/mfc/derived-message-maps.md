---
title: Mapas de mensajes derivados
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 0868b12720cfa338ab7275a358e065506adc11d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615913"
---
# <a name="derived-message-maps"></a>Mapas de mensajes derivados

Durante el control de mensajes, la comprobación del mapa de mensajes de una clase no es el final del caso del mapa de mensajes. Qué sucede si la clase `CMyView` (derivada de `CView` ) no tiene ninguna entrada coincidente para un mensaje

Tenga en cuenta que `CView` , a su vez, la clase base de `CMyView` se deriva de `CWnd` . Por lo tanto, `CMyView` *es* `CView` y *es* `CWnd` . Cada una de esas clases tiene su propio mapa de mensajes. La ilustración siguiente muestra la relación jerárquica de las clases, pero tenga en cuenta que un `CMyView` objeto es un objeto único que tiene las características de las tres clases.

![Jerarquía de una vista](../mfc/media/vc38621.gif "Jerarquía de una vista") <br/>
Una jerarquía de vistas

Por tanto, si no se puede hacer coincidir un mensaje en el mapa de mensajes de la clase `CMyView` , el marco de trabajo también busca en el mapa de mensajes de su clase base inmediata. La `BEGIN_MESSAGE_MAP` macro del inicio del mapa de mensajes especifica dos nombres de clase como argumentos:

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

El primer argumento nombra la clase a la que pertenece el mapa de mensajes. El segundo argumento proporciona una conexión con la clase base inmediata ( `CView` aquí), por lo que el marco también puede buscar en su mapa de mensajes.

Por lo tanto, la clase derivada hereda los controladores de mensajes proporcionados en una clase base. Esto es muy similar a las funciones miembro virtuales normales sin necesidad de hacer que todas las funciones miembro del controlador sean virtuales.

Si no se encuentra ningún controlador en ninguno de los mapas de mensajes de clase base, se realiza el procesamiento predeterminado del mensaje. Si el mensaje es un comando, el marco lo enruta al siguiente destino del comando. Si es un mensaje de Windows estándar, el mensaje se pasa al procedimiento de ventana predeterminado adecuado.

Para acelerar la coincidencia del mapa de mensajes, el marco de trabajo almacena en caché las coincidencias recientes en la probabilidad de que reciba el mismo mensaje de nuevo. Una consecuencia de esto es que el marco de trabajo procesa los mensajes no controlados de forma muy eficaz. Los mapas de mensajes también son más eficientes que las implementaciones que usan funciones virtuales.

## <a name="see-also"></a>Consulte también

[Cómo busca el marco los mapas de mensajes](how-the-framework-searches-message-maps.md)
