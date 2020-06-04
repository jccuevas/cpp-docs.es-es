---
title: Dónde buscar mapas de mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: eec0ae43546e3cc0c08e3178c4808e21fa48686a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360161"
---
# <a name="where-to-find-message-maps"></a>Dónde buscar mapas de mensajes

Al crear una nueva aplicación de esqueleto con el Asistente para aplicaciones, el Asistente para aplicaciones escribe un mapa de mensajes para cada clase de destino de comando que crea automáticamente. Esto incluye las clases derivadas de aplicación, documento, vista y ventana de marco. Algunos de estos mapas de mensajes ya tienen las entradas proporcionadas por el Asistente para aplicaciones para determinados mensajes y comandos predefinidos, y algunos son solo marcadores de posición para los controladores que agregará.

El mapa de mensajes de una clase se encuentra en el archivo . CPP para la clase. Al trabajar con los mapas de mensajes básicos que crea el Asistente para aplicaciones, utilice el [Asistente para](reference/mfc-class-wizard.md) clases para agregar entradas para los mensajes y comandos que controlará cada clase. Un mapa de mensajes típico podría tener el siguiente aspecto después de agregar algunas entradas:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

El mapa de mensajes consta de una colección de macros. Dos macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) y [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), entre corchetes el mapa de mensajes. Otras macros, `ON_COMMAND`como , rellenan el contenido del mapa de mensajes.

> [!NOTE]
> Las macros de mapa de mensajes no van seguidas de punto y coma.

Cuando se utiliza el Asistente para agregar clase para crear una nueva clase, proporciona un mapa de mensajes para la clase. Como alternativa, puede crear un mapa de mensajes manualmente mediante el editor de código fuente.

## <a name="see-also"></a>Consulte también

[Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)
