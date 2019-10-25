---
title: Dónde buscar mapas de mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: c50c6fc1134f579859530972dc864103c4e0ebcf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907369"
---
# <a name="where-to-find-message-maps"></a>Dónde buscar mapas de mensajes

Cuando se crea una nueva aplicación de esqueleto con el Asistente para aplicaciones, el Asistente para aplicaciones escribe un mapa de mensajes para cada clase de destino de comando que crea automáticamente. Esto incluye las clases derivadas de la aplicación, el documento, la vista y la ventana de marco. Algunos de estos mapas de mensajes ya tienen las entradas proporcionadas por el Asistente para aplicaciones para determinados mensajes y comandos predefinidos, y algunos son solo marcadores de posición para los controladores que se van a agregar.

El mapa de mensajes de una clase se encuentra en. Archivo CPP para la clase. Al trabajar con los mapas de mensajes básicos que crea el Asistente para aplicaciones, se usa el [Asistente para clases](reference/mfc-class-wizard.md) para agregar entradas para los mensajes y comandos que controlará cada clase. Un mapa de mensajes típico podría tener un aspecto similar al siguiente después de agregar algunas entradas:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

El mapa de mensajes se compone de una colección de macros. Dos macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) y [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), corcheten el mapa de mensajes. Otras macros, como `ON_COMMAND`, rellenan el contenido del mapa de mensajes.

> [!NOTE]
>  Las macros de mapa de mensajes no van seguidas de punto y coma.

Cuando se usa el Asistente para agregar clases para crear una nueva clase, proporciona un mapa de mensajes para la clase. También puede crear un mapa de mensajes manualmente mediante el editor de código fuente.

## <a name="see-also"></a>Vea también

[Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)
