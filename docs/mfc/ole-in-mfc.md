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
ms.openlocfilehash: 2668d35c24e9d95440a96c5b3eda1fab7bbf3891
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507996"
---
# <a name="ole-in-mfc"></a>OLE en MFC

En estos artículos se explican los aspectos básicos de la programación OLE con MFC. MFC proporciona la forma más sencilla de escribir programas que utilizan OLE:

- Para usar la edición visual OLE (activación en contexto).

- Para trabajar como servidores o contenedores OLE.

- Para implementar la funcionalidad de arrastrar y colocar.

- Trabajar con datos de fecha y hora.

- Administrar los datos de estado de los módulos MFC, incluidos los puntos de entrada de función DLL exportados, los puntos de entrada de la interfaz OLE/COM y los puntos de entrada de procedimiento de ventana.

También puede utilizar la [automatización](../mfc/automation.md).

> [!NOTE]
>  El término OLE denota las tecnologías asociadas a la vinculación e incrustación, incluidos contenedores OLE, servidores OLE, elementos OLE, activación en contexto (o edición visual), rastreadores, arrastrar y colocar y combinación de menús. El término activo se aplica a los objetos de modelo de objetos componentes (COM) y basados en COM, como los controles ActiveX. La automatización OLE se denomina ahora automatización.

## <a name="in-this-section"></a>En esta sección

[Nociones de OLE](../mfc/ole-background.md)<br/>
Describe OLE y proporciona información conceptual sobre cómo funciona.

[Activación](../mfc/activation-cpp.md)<br/>
Describe el rol de activación en la edición de elementos OLE.

[Contenedores](../mfc/containers.md)<br/>
Proporciona vínculos al uso de contenedores en OLE.

[Objetos de datos y orígenes de datos](../mfc/data-objects-and-data-sources-ole.md)<br/>
Proporciona vínculos a temas en los que se describe `COleDataObject` el `COleDataSource` uso de las clases y.

[Arrastrar y colocar](../mfc/drag-and-drop-ole.md)<br/>
Describe el uso de copiar y pegar con OLE.

[Menús y recursos OLE](../mfc/menus-and-resources-ole.md)<br/>
Explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

[Registro](../mfc/registration.md)<br/>
Describe la instalación y la inicialización del servidor.

[Servidores](../mfc/servers.md)<br/>
Describe cómo crear elementos OLE (o componentes) para su uso por parte de aplicaciones contenedoras.

[Seguimiento](../mfc/trackers.md)<br/>
Proporciona información sobre la `CRectTracker` clase, que proporciona una interfaz gráfica que permite a los usuarios interactuar con elementos de cliente OLE.

## <a name="related-sections"></a>Secciones relacionadas

[Puntos de conexión](../mfc/connection-points.md)<br/>
Explica cómo implementar puntos de conexión (antes conocidos como puntos de conexión OLE) mediante las clases `CCmdTarget` MFC `CConnectionPoint`y.

[Componentes COM de contenedor/servidor](../mfc/containers-advanced-features.md)<br/>
Describe los pasos necesarios para incorporar características avanzadas opcionales en aplicaciones de contenedor existentes.

[The Component Object Model](/windows/win32/com/the-component-object-model) [Modelo de objetos componentes (COM)]<br/>
Describe el uso de OLE sin MFC.

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)
