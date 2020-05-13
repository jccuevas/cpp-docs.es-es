---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: 514251475050e728be1959417ead1dbdf96e4800
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358192"
---
# <a name="mfc-com"></a>MFC COM

Un subconjunto de MFC está diseñado para admitir COM, mientras que la mayor parte de la biblioteca de plantillas activas (ATL) está diseñada para la programación COM. En esta sección de temas se describe la compatibilidad de MFC con COM.

Las tecnologías activas (como controles ActiveX, contención de documentos activos, OLE, etc.) usan el modelo de objetos componentes (COM) para permitir que los componentes de software interactúen entre sí en un entorno en red, independientemente del idioma con el que se crearon. Las tecnologías activas se pueden utilizar para crear aplicaciones que se ejecutan en el escritorio o en Internet. Para obtener más información, consulte [Introducción a COM](../atl/introduction-to-com.md) o [El modelo de objetos componentes](/windows/win32/com/the-component-object-model).

Las tecnologías activas incluyen tecnologías de cliente y servidor, incluidas las siguientes:

- Los controles ActiveX son objetos interactivos que se pueden usar en contenedores como un sitio Web. Para obtener más información sobre los controles ActiveX, consulte:

  - [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

  - [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)

  - [Resumen: Internet](../mfc/mfc-internet-programming-basics.md)

  - [Actualice un control ActiveX existente para utilizarlo en Internet](../mfc/upgrading-an-existing-activex-control.md)

  - [Depuración de un control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- El scripting activo controla el comportamiento integrado de uno o más controles ActiveX desde un explorador o servidor. Para obtener más información sobre el scripting activo, consulte [Tecnología activa en Internet](../mfc/active-technology-on-the-internet.md).

- [La automatización](../mfc/automation.md) (anteriormente conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o "exponga" objetos para que se puedan manipular.

   El objeto automatizado puede ser local o remoto (en otro equipo accesible a través de una red). La automatización está disponible para objetos COM y OLE.

- Esta sección también proporciona información sobre cómo escribir componentes COM mediante MFC, por ejemplo, en [Puntos](../mfc/connection-points.md)de conexión .

Para obtener una explicación de lo que todavía se llama OLE frente a lo que ahora se llama tecnología activa, vea los temas sobre [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>En esta sección

[Contención de documentos activos](../mfc/active-document-containment.md)

[Automation](../mfc/automation.md)

[Puntos de conexión](../mfc/connection-points.md)

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Consulte también

[Conceptos](../mfc/mfc-concepts.md)
