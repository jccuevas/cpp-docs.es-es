---
title: Dónde buscar mapas de mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
ms.openlocfilehash: d9b9a50062334822f34047b8e22e67541ccaa952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217867"
---
# <a name="where-to-find-message-maps"></a>Dónde buscar mapas de mensajes

Cuando se crea una nueva aplicación de esqueleto con el Asistente para aplicaciones, el Asistente para la aplicación escribe un mapa de mensajes para cada clase de destino del comando que crea para usted. Esto incluye su aplicación derivada, documento, vista y las clases de ventana de marco. Algunos de estos mapas de mensajes que ya tienen entradas suministradas por el Asistente para aplicaciones para determinados mensajes y comandos predefinidos, y algunas son sólo marcadores de posición para los controladores que va a agregar.

Mapa de mensajes de una clase se encuentra en el. Archivo CPP para la clase. Trabajar con los mapas de mensajes básica que crea el Asistente para aplicaciones, utilice la ventana Propiedades para agregar entradas para los mensajes y comandos que se va a controlar cada clase. Un mapa de mensajes típico podría ser similar al siguiente después de agregar algunas entradas:

[!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]

El mapa de mensajes consta de una colección de macros. Las dos macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) y [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), el mapa de mensajes de los corchetes. Otras macros, como `ON_COMMAND`, rellene el contenido del mapa de mensajes.

> [!NOTE]
>  No se siguen las macros de mapa de mensajes por punto y coma.

Cuando usa el Asistente para agregar clases para crear una nueva clase, proporciona un mapa de mensajes para la clase. Como alternativa, puede crear un mapa de mensajes manualmente mediante el editor de código fuente.

## <a name="see-also"></a>Vea también

[Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)
