---
title: "OLE en MFC | Microsoft Docs"
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
  - "aplicaciones [OLE], acerca de OLE"
  - "MFC [C++], OLE y"
  - "OLE [C++]"
  - "aplicaciones OLE [C++], acerca de OLE"
  - "modelo de objetos componentes de OLE (COM)"
  - "contenedores OLE, acerca de OLE"
  - "elementos OLE"
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estos casos explican los fundamentos de la programación OLE con MFC.  MFC proporciona la manera más fácil de escribir programas que utilizan OLE:  
  
-   Para utilizar la edición visual OLE \(activación en contexto\).  
  
-   Para trabajar con los contenedores de OLE o servidores.  
  
-   Para implementar la funcionalidad de arrastrar y colocar.  
  
-   Para trabajar con datos de fecha y hora.  
  
-   Para administrar los datos de estado de los módulos MFC, como puntos de entrada exportados de los puntos de entrada de la función DLL, la interfaz OLE y COM, y puntos de entrada del procedimiento de ventana.  
  
 También puede utilizar [Automatización](../mfc/automation.md) o [Automatización remota](../mfc/remote-automation.md) funcione otro programa del programa.  
  
> [!NOTE]
>  El término OLE indica las tecnologías asociadas a vincular y a insertar, incluidos los contenedores de OLE, los servidores OLE, los elementos de OLE, la activación en contexto \(o edición visual\), los rastreadores, arrastrar y colocar, y la combinación de menús.  El activo del término se aplica al modelo de objetos componentes \(COM\) y objetos basado en COM como controles ActiveX.  Automatización OLE ahora se denomina Automation.  
  
## En esta sección  
 [Fondo OLE](../mfc/ole-background.md)  
 Describe OLE y proporciona información conceptual sobre cómo funciona.  
  
 [Activación](../mfc/activation-cpp.md)  
 Describe el rol de la activación de modificar los elementos de OLE.  
  
 [Contenedores](../mfc/containers.md)  
 Proporciona vínculos a usar contenedores de OLE.  
  
 [Objetos de datos y orígenes de datos](../mfc/data-objects-and-data-sources-ole.md)  
 Proporciona vínculos a temas que explican el uso de las clases de `COleDataObject` y de `COleDataSource` .  
  
 [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
 Describe el uso de copiar y pegar con OLE.  
  
 [Menús de OLE y recursos](../mfc/menus-and-resources-ole.md)  
 Explica el uso de menús y recursos en aplicaciones VIEJAS de documento de MFC.  
  
 [Registro](../mfc/registration.md)  
 Describe la instalación y la inicialización del servidor.  
  
 [Servidores](../mfc/servers.md)  
 Describe cómo crear elementos de OLE \(o componentes\) para uso de aplicaciones contenedoras.  
  
 [Rastreadores](../mfc/trackers.md)  
 Proporciona información sobre la clase de `CRectTracker` , que proporciona una interfaz gráfica que permitan a los usuarios interactuar con los elementos de OLE de cliente.  
  
## Secciones relacionadas  
 [Puntos de conexión](../mfc/connection-points.md)  
 Explica cómo implementar puntos de conexión \(anteriormente conocido como puntos de conexión de OLE\) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.  
  
 [Componentes COM de contenedor\/Servidor](../mfc/containers-advanced-features.md)  
 Describe los pasos necesarios para especificar características avanzadas opcionales en aplicaciones contenedoras existentes.  
  
 [El modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Describe mediante OLE sin MFC.  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)