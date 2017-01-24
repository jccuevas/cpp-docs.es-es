---
title: "Nociones de OLE: Estrategias de implementaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [OLE], implementar OLE"
  - "OLE [C++], estrategia de desarrollo"
  - "aplicaciones OLE [C++], implementar OLE"
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Nociones de OLE: Estrategias de implementaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dependiendo de la aplicación, hay cuatro estrategias de implementación posibles para agregar OLE admite:  
  
-   Escribe una nueva aplicación.  
  
     Esta situación requiere normalmente el menos trabajo.  Ejecute el Asistente para aplicaciones MFC y seleccionar características avanzadas o compatibilidad de documento compuesto para crear una aplicación esqueleto.  Para obtener información sobre estas opciones y qué hace, vea el artículo [Crear un programa MFC EXE](../mfc/reference/mfc-application-wizard.md).  
  
-   Tiene un programa escrito con la versión 2.0 de la biblioteca Microsoft Foundation Class o superior que no admite OLE.  
  
     Cree una nueva aplicación con el asistente para aplicaciones MFC como se mencionó anteriormente, y luego volver y pegue el código de aplicación en la aplicación existente.  Esto funcionará con los servidores, los contenedores, o aplicaciones automatizadas.  Vea el ejemplo de MFC [SCRIBBLE](../top/visual-cpp-samples.md) para obtener un ejemplo de esta estrategia.  
  
-   Tiene un programa de biblioteca MFC \(Microsoft Foundation Class\) que implementa la compatibilidad con la versión 1.0 de OLE.  
  
     Vea [Nota técnica 41 de MFC](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) para esta estrategia de conversión.  
  
-   Tiene una aplicación que no se escritas con Microsoft Foundation Classes y que puede o no puede haber implementado compatibilidad OLE.  
  
     Esta situación requiere la mayoría del trabajo.  Un enfoque consiste en crear una nueva aplicación, como en la primera estrategia, y luego copie y pegue el código existente en él.  Si el código existente está escrita en C, puede que tenga que modificarlo para que pueda compilar como código de C\+\+.  Si el código de C llama a la API de Windows, no tiene que modificar para utilizar las clases de la Microsoft foundation class.  Este enfoque requerirá probablemente alguna reestructuración de programa admitir la arquitectura documento\/vista utilizada por las versiones 2.0 y superior de Microsoft Foundation Classes.  Para obtener más información sobre esta arquitectura, vea [Nota técnica 25](../mfc/tn025-document-view-and-frame-creation.md).  
  
 Una vez que haya decidido sobre una estrategia, lea los casos de [Contenedores](../mfc/containers.md) o de [servidores](../mfc/servers.md) \(según el tipo de aplicación que está escribiendo\) o examinar los programas de ejemplo, o ambos.  Los ejemplos [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md) MFC OLE muestran cómo implementar los distintos aspectos de contenedores y de servidores, respectivamente.  En varios puntos en estos casos, será determinadas funciones relacionadas en estos ejemplos como ejemplos de las técnicas que son descritas.  
  
## Vea también  
 [Nociones de OLE](../mfc/ole-background.md)   
 [Contenedores: Implementar un contenedor](../mfc/containers-implementing-a-container.md)   
 [Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)   
 [Asistente para aplicaciones MFC](../mfc/reference/mfc-application-wizard.md)