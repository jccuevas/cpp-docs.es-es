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
ms.openlocfilehash: 2594531df63bcd62cdaec44fbc3668ea68990922
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366894"
---
# <a name="ole-in-mfc"></a>OLE en MFC

Estos artículos explican los fundamentos de la programación OLE mediante MFC. MFC proporciona la forma más fácil de escribir programas que usan OLE:

- Para usar la edición visual OLE (activación in situ).

- Para trabajar como contenedores OLE o servidores.

- Para implementar la funcionalidad de arrastrar y colocar.

- Para trabajar con datos de fecha y hora.

- Para administrar los datos de estado de los módulos MFC, incluidos los puntos de entrada de función DLL exportados, los puntos de entrada de interfaz OLE/COM y los puntos de entrada de procedimiento de ventana.

También puede utilizar [Automatización](../mfc/automation.md).

> [!NOTE]
> El término OLE denota las tecnologías asociadas con la vinculación y la incrustación, incluidos los contenedores OLE, los servidores OLE, los elementos OLE, la activación en contexto (o la edición visual), los rastreadores, la arrastrar y colocar y la combinación de menús. El término Activo se aplica al modelo de objetos componentes (COM) y a los objetos basados en COM, como los controles ActiveX. La automatización OLE ahora se denomina automatización.

## <a name="in-this-section"></a>En esta sección

[Nociones de OLE](../mfc/ole-background.md)<br/>
Describe OLE y proporciona información conceptual sobre cómo funciona.

[Activación](../mfc/activation-cpp.md)<br/>
Describe el rol de activación en la edición de elementos OLE.

[Contenedores](../mfc/containers.md)<br/>
Proporciona vínculos al uso de contenedores en OLE.

[Objetos de datos y orígenes de datos](../mfc/data-objects-and-data-sources-ole.md)<br/>
Proporciona vínculos a temas que `COleDataObject` `COleDataSource` tratan el uso de las clases.

[Arrastrar y colocar](../mfc/drag-and-drop-ole.md)<br/>
Describe el uso de copiar y pegar con OLE.

[Menús y recursos OLE](../mfc/menus-and-resources-ole.md)<br/>
Explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

[Registro](../mfc/registration.md)<br/>
Describe la instalación y la inicialización del servidor.

[Servidores](../mfc/servers.md)<br/>
Describe cómo crear elementos OLE (o componentes) para su uso por las aplicaciones contenedoras.

[Seguimiento](../mfc/trackers.md)<br/>
Proporciona información `CRectTracker` sobre la clase, que proporciona una interfaz gráfica para permitir a los usuarios interactuar con elementos de cliente OLE.

## <a name="related-sections"></a>Secciones relacionadas

[Puntos de conexión](../mfc/connection-points.md)<br/>
Explica cómo implementar puntos de conexión (anteriormente conocidos como puntos de conexión OLE) mediante las clases `CCmdTarget` MFC y `CConnectionPoint`.

[Componentes COM de contenedor/servidor](../mfc/containers-advanced-features.md)<br/>
Describe los pasos necesarios para incorporar características avanzadas opcionales en las aplicaciones de contenedor existentes.

[The Component Object Model](/windows/win32/com/the-component-object-model) [Modelo de objetos componentes (COM)]<br/>
Describe el uso de OLE sin MFC.

## <a name="see-also"></a>Consulte también

[Conceptos](../mfc/mfc-concepts.md)
