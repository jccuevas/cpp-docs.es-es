---
title: Dónde buscar mapas de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, message map
- locating message maps
- message classes [MFC], finding
- message-map macros
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19dfaec7d97bed560665fce25c2ddf2cc816a483
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="where-to-find-message-maps"></a>Dónde buscar mapas de mensajes
Cuando se crea una nueva aplicación esquema con el Asistente para aplicaciones, el Asistente para la aplicación escribe un mapa de mensajes para cada clase de destino del comando que crea para usted. Esto incluye la aplicación derivada, documento, vista y las clases de ventana de marco. Algunos de estos mapas de mensajes ya disponen de entradas suministradas por el Asistente para aplicaciones para determinados mensajes y comandos predefinidos, y otras son simplemente los marcadores de posición para los controladores que va a agregar.  
  
 Mapa de mensajes de una clase se encuentra en el. Archivo CPP de la clase. Trabajar con los mapas de mensajes básicos que crea el Asistente para aplicaciones, utilice la ventana Propiedades para agregar entradas para los mensajes y comandos que va a controlar cada clase. Un mapa de mensajes típico podría ser similar al siguiente después de agregar algunas entradas:  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/cpp/where-to-find-message-maps_1.cpp)]  
  
 El mapa de mensajes consta de una colección de macros. Las dos macros, [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) y [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map), poner entre corchetes el mapa de mensajes. Otras macros, como `ON_COMMAND`, rellene el contenido del mapa de mensajes.  
  
> [!NOTE]
>  Las macros de mapa de mensajes no van seguidas de punto y coma.  
  
 Cuando usa el Asistente para agregar clases para crear una nueva clase, proporciona un mapa de mensajes para la clase. Como alternativa, puede crear un mapa de mensajes manualmente mediante el editor de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)

