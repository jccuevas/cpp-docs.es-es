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
ms.openlocfilehash: eab688022c311f3d20fc092736ee4c7d37232a43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508089"
---
# <a name="mfc-com"></a>MFC COM

Un subconjunto de MFC se ha diseñado para admitir COM, mientras que la mayoría de los Active Template Library (ATL) están diseñados para la programación COM. En esta sección de temas se describe la compatibilidad de MFC con COM.

Las tecnologías activas (como los controles ActiveX, la contención de documentos activos, OLE, etc.) usan el modelo de objetos componentes (COM) para permitir que los componentes de software interactúen entre sí en un entorno en red, independientemente del idioma con el que se encontraran. creado. Las tecnologías activas se pueden usar para crear aplicaciones que se ejecutan en el escritorio o en Internet. Para obtener más información, vea [Introducción a com](../atl/introduction-to-com.md) o [el modelo de objetos componentes](/windows/win32/com/the-component-object-model).

Las tecnologías activas incluyen tecnologías de cliente y de servidor, incluidas las siguientes:

- Los controles ActiveX son objetos interactivos que se pueden utilizar en contenedores como un sitio Web. Para obtener más información sobre los controles ActiveX, vea:

   - [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

   - [Controles ActiveX en Internet](../mfc/activex-controls-on-the-internet.md)

   - [Información general: Internet](../mfc/mfc-internet-programming-basics.md)

   - [Actualizar un control ActiveX existente para su uso en Internet](../mfc/upgrading-an-existing-activex-control.md)

   - [Depurar un control ActiveX](/visualstudio/debugger/how-to-debug-an-activex-control)

- Active Scripting controla el comportamiento integrado de uno o más controles ActiveX desde un explorador o un servidor. Para obtener más información sobre Active Scripting, vea [tecnología activa en Internet](../mfc/active-technology-on-the-internet.md).

- [Automatización](../mfc/automation.md) de (antes conocida como automatización OLE) permite que una aplicación manipule objetos implementados en otra aplicación o "exponga" objetos para que se puedan manipular.

   El objeto automatizado puede ser local o remoto (en otra máquina accesible a través de una red). La automatización está disponible para objetos COM y OLE.

- En esta sección también se proporciona información sobre cómo escribir componentes COM mediante MFC, por ejemplo, en [puntos de conexión](../mfc/connection-points.md).

Para obtener una explicación de lo que se sigue llamando OLE frente a lo que ahora se denomina tecnología activa, vea los temas sobre [OLE](../mfc/ole-in-mfc.md).

## <a name="in-this-section"></a>En esta sección

[Contención de documentos activos](../mfc/active-document-containment.md)

[Automatización](../mfc/automation.md)

[Puntos de conexión](../mfc/connection-points.md)

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)
