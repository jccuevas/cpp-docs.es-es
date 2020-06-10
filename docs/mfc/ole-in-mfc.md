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
ms.openlocfilehash: 529b6d0eaedaee200da547ef9ed980aab51ea233
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622173"
---
# <a name="ole-in-mfc"></a>OLE en MFC

En estos artículos se explican los aspectos básicos de la programación OLE con MFC. MFC proporciona la forma más sencilla de escribir programas que utilizan OLE:

- Para usar la edición visual OLE (activación en contexto).

- Para trabajar como servidores o contenedores OLE.

- Para implementar la funcionalidad de arrastrar y colocar.

- Trabajar con datos de fecha y hora.

- Administrar los datos de estado de los módulos MFC, incluidos los puntos de entrada de función DLL exportados, los puntos de entrada de la interfaz OLE/COM y los puntos de entrada de procedimiento de ventana.

También puede utilizar la [automatización](automation.md).

> [!NOTE]
> El término OLE denota las tecnologías asociadas a la vinculación e incrustación, incluidos contenedores OLE, servidores OLE, elementos OLE, activación en contexto (o edición visual), rastreadores, arrastrar y colocar y combinación de menús. El término activo se aplica a los objetos de modelo de objetos componentes (COM) y basados en COM, como los controles ActiveX. La automatización OLE se denomina ahora automatización.

## <a name="in-this-section"></a>En esta sección

[Nociones de OLE](ole-background.md)<br/>
Describe OLE y proporciona información conceptual sobre cómo funciona.

[Activación](activation-cpp.md)<br/>
Describe el rol de activación en la edición de elementos OLE.

[Contenedores](containers.md)<br/>
Proporciona vínculos al uso de contenedores en OLE.

[Objetos de datos y orígenes de datos](data-objects-and-data-sources-ole.md)<br/>
Proporciona vínculos a temas en los que se describe el uso de las `COleDataObject` `COleDataSource` clases y.

[Arrastrar y colocar](drag-and-drop-ole.md)<br/>
Describe el uso de copiar y pegar con OLE.

[Menús y recursos OLE](menus-and-resources-ole.md)<br/>
Explica el uso de menús y recursos en aplicaciones de documentos OLE de MFC.

[Registro](registration.md)<br/>
Describe la instalación y la inicialización del servidor.

[Servidores](servers.md)<br/>
Describe cómo crear elementos OLE (o componentes) para su uso por parte de aplicaciones contenedoras.

[Seguimiento](trackers.md)<br/>
Proporciona información sobre la `CRectTracker` clase, que proporciona una interfaz gráfica que permite a los usuarios interactuar con elementos de cliente OLE.

## <a name="related-sections"></a>Secciones relacionadas

[Puntos de conexión](connection-points.md)<br/>
Explica cómo implementar puntos de conexión (antes conocidos como puntos de conexión OLE) mediante las clases MFC `CCmdTarget` y `CConnectionPoint` .

[Componentes COM de contenedor/servidor](containers-advanced-features.md)<br/>
Describe los pasos necesarios para incorporar características avanzadas opcionales en aplicaciones de contenedor existentes.

[The Component Object Model](/windows/win32/com/the-component-object-model) [Modelo de objetos componentes (COM)]<br/>
Describe el uso de OLE sin MFC.

## <a name="see-also"></a>Consulte también

[Conceptos](mfc-concepts.md)
