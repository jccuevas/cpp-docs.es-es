---
title: "D&#243;nde buscar mapas de mensajes | Microsoft Docs"
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
  - "localizar mapas de mensajes"
  - "macros, asignación de mensajes"
  - "mapas de mensajes, buscar"
  - "macros de mapa de mensajes"
ms.assetid: bf59fbc8-b222-42d3-b5d3-0a79aa3cb923
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# D&#243;nde buscar mapas de mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear una nueva aplicación esqueleto con el Asistente para aplicaciones, el Asistente para aplicaciones escribe un mapa de mensajes para cada clase de comando\- destino que crea automáticamente.  Esto incluye la aplicación, el documento, la vista, y las clases derivadas de la cuadro\- ventana.  Algunos de estos mapas de mensajes ya tienen las entradas proporcionadas por los mensajes del Asistente para aplicaciones para ciertos y comandos predefinidos, y otras son solo marcadores de posición para los controladores que agregará.  
  
 El mapa de mensajes de una clase se encuentra en el archivo de .CPP para la clase.  Trabajar con los mapas básicos de mensajes que el Asistente para aplicaciones crea, utiliza la ventana Propiedades para agregar las entradas para los mensajes y los comandos que cada clase controlará.  Un mapa típico del mensaje podría tener el aspecto siguiente después de agregar algunas entradas:  
  
 [!code-cpp[NVC_MFCMessageHandling#1](../mfc/codesnippet/CPP/where-to-find-message-maps_1.cpp)]  
  
 El mapa de mensajes se compone de una colección de macros.  Dos macros, [BEGIN\_MESSAGE\_MAP](../Topic/BEGIN_MESSAGE_MAP.md) y [END\_MESSAGE\_MAP](../Topic/END_MESSAGE_MAP.md), corchete el mapa de mensajes.  Otras macros, como `ON_COMMAND`, completar el contenido del mapa de mensajes.  
  
> [!NOTE]
>  Las macros de mensaje\- mapa no van seguidas de puntos y coma.  
  
 Cuando se utiliza el asistente para la clase add para crear una nueva clase, proporciona un mensaje asignado para la clase.  Alternativamente, puede crear un mapa de mensajes manualmente mediante el editor de código fuente.  
  
## Vea también  
 [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)