---
title: OLE en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 992715c545f90176ab750890c4be3e05dfe950d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520489"
---
# <a name="ole-in-mfc"></a>OLE en MFC

Estos artículos explican los aspectos básicos de programación de OLE mediante MFC. MFC proporciona la manera más fácil de escribir programas que utilizan OLE:

- Para usar OLE visual edición (activación en contexto).

- Para que funcione como contenedores o servidores OLE.

- Para implementar la funcionalidad de arrastrar y colocar.

- Para trabajar con datos de fecha y hora.

- Para administrar los datos de estado de MFC módulos, incluidos exportan puntos de entrada de función DLL, puntos de entrada de interfaz OLE/COM y los puntos de entrada de procedimiento de ventana.

También puede usar [automatización](../mfc/automation.md).

> [!NOTE]
>  El término que OLE denota las tecnologías asociadas con la vinculación e incrustación de objetos, incluidos contenedores OLE, servidores OLE, elementos OLE, activación en contexto (o edición visual), objetos de seguimiento, arrastrar y colocar y combinación de menús. El término activo se aplica al modelo de objetos componentes (COM) y objetos basados en COM, como controles ActiveX. OLE Automation ahora se llama a la automatización.

## <a name="in-this-section"></a>En esta sección

[Nociones de OLE](../mfc/ole-background.md)<br/>
Describe OLE y proporciona información conceptual acerca de cómo funciona.

[Activación](../mfc/activation-cpp.md)<br/>
Describe la función de activación en la edición de elementos OLE.

[Contenedores](../mfc/containers.md)<br/>
Proporciona vínculos a uso de contenedores en OLE.

[Objetos de datos y orígenes de datos](../mfc/data-objects-and-data-sources-ole.md)<br/>
Proporciona vínculos a temas que describen el uso de la `COleDataObject` y `COleDataSource` clases.

[Arrastrar y colocar](../mfc/drag-and-drop-ole.md)<br/>
Describe el uso de copiar y pegar con OLE.

[Menús y recursos OLE](../mfc/menus-and-resources-ole.md)<br/>
Explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

[Registro](../mfc/registration.md)<br/>
Describe la inicialización y la instalación del servidor.

[Servidores](../mfc/servers.md)<br/>
Describe cómo crear elementos OLE (o componentes) para su uso por aplicaciones de contenedor.

[Seguimiento](../mfc/trackers.md)<br/>
Proporciona información sobre la `CRectTracker` (clase), que proporciona una interfaz gráfica que permite a los usuarios interactuar con elementos de cliente OLE.

## <a name="related-sections"></a>Secciones relacionadas

[Puntos de conexión](../mfc/connection-points.md)<br/>
Se explica cómo implementar puntos de conexión (conocidos anteriormente como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint`.

[Componentes de contenedor y servidor COM](../mfc/containers-advanced-features.md)<br/>
Describe los pasos necesarios para incorporar características avanzadas adicionales a las aplicaciones existentes de contenedor.

[The Component Object Model](/windows/desktop/com/the-component-object-model) [Modelo de objetos componentes (COM)]<br/>
Describe cómo usar OLE sin MFC.

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)

