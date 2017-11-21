---
title: OLE en MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2a7fcd7db19d9dcc6e12c351a3fd55f0e67b118
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ole-in-mfc"></a>OLE en MFC
Estos artículos explican los conceptos básicos de programación de OLE mediante MFC. MFC proporciona la manera más fácil de escribir programas que utilizan OLE:  
  
-   Para usar OLE visual edición (activación en contexto).  
  
-   Funcionar como contenedores o servidores OLE.  
  
-   Para implementar la funcionalidad de arrastrar y colocar.  
  
-   Para trabajar con datos de fecha y hora.  
  
-   Para administrar los datos de estado de MFC módulos, incluidos exportan puntos de entrada de función DLL, puntos de entrada de interfaz OLE/COM y los puntos de entrada de procedimiento de ventana.  
  
 También puede usar [automatización](../mfc/automation.md) o [automatización remota](../mfc/remote-automation.md) para ejecutar otro programa desde su programa.  
  
> [!NOTE]
>  El término que OLE denota las tecnologías asociadas con vinculación e incrustación de objetos, incluidos los contenedores OLE, servidores OLE, elementos OLE, activación en contexto (o edición visual), objetos de seguimiento, arrastrar y colocar y la combinación de menús. El término activo se aplica a los objetos basados en COM y el modelo de objetos componentes (COM), como controles ActiveX. Automatización OLE se denomina ahora automatización.  
  
## <a name="in-this-section"></a>En esta sección  
 [Nociones de OLE](../mfc/ole-background.md)  
 Describe OLE y proporciona información conceptual acerca de cómo funciona.  
  
 [Activación](../mfc/activation-cpp.md)  
 Describe el rol de la activación en la edición de elementos OLE.  
  
 [Contenedores](../mfc/containers.md)  
 Proporciona vínculos sobre cómo utilizar contenedores en OLE.  
  
 [Objetos de datos y orígenes de datos](../mfc/data-objects-and-data-sources-ole.md)  
 Proporciona vínculos a temas que describen el uso de la `COleDataObject` y `COleDataSource` clases.  
  
 [Arrastrar y colocar](../mfc/drag-and-drop-ole.md)  
 Describe el uso de copiar y pegar con OLE.  
  
 [Menús y recursos OLE](../mfc/menus-and-resources-ole.md)  
 Explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.  
  
 [Registro](../mfc/registration.md)  
 Describe la inicialización y la instalación del servidor.  
  
 [Servidores](../mfc/servers.md)  
 Describe cómo crear elementos OLE (o componentes) para su uso por aplicaciones de contenedor.  
  
 [Seguimiento](../mfc/trackers.md)  
 Proporciona información sobre la `CRectTracker` (clase), que proporciona una interfaz gráfica para habilitar a los usuarios interactuar con elementos de cliente OLE.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Puntos de conexión](../mfc/connection-points.md)  
 Explica cómo implementar puntos de conexión (que antes de que se conocía como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.  
  
 [Componentes COM contenedor/servidor](../mfc/containers-advanced-features.md)  
 Describe los pasos necesarios para incorporar características avanzadas adicionales a aplicaciones contenedoras existentes.  
  
 [El modelo de objetos componentes](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Describe cómo utilizar OLE sin MFC.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)

