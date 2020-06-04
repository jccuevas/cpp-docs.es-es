---
title: Crear nuevos documentos, ventanas y vistas
ms.date: 11/19/2018
helpviewer_keywords:
- MDI [MFC], creating windows
- window objects [MFC], creating
- objects [MFC], creating document objects
- MFC default objects
- frame windows [MFC], creating
- windows [MFC], MDI
- MFC, documents
- view objects [MFC], creating
- windows [MFC], creating
- overriding, default view behavior
- views [MFC], initializing
- customizing MFC default objects
- MFC, frame windows
- MFC, views
- MDI [MFC], frame windows
- child windows [MFC], creating MDI
- view objects [MFC]
- document objects [MFC], creating
- MFC default objects [MFC], customizing
- views [MFC], overriding default behavior
- initializing views [MFC]
ms.assetid: 88aa1f5f-2078-4603-b16b-a2b4c7b4a2a3
ms.openlocfilehash: aa1c58b02df92d79ca9915032b97fb5c0e2eaffc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371665"
---
# <a name="creating-new-documents-windows-and-views"></a>Crear nuevos documentos, ventanas y vistas

Las figuras siguientes proporcionan una visión general del proceso de creación de documentos, vistas y ventanas de marco. Otros artículos que se centran en los objetos participantes proporcionan más detalles.

Al finalizar este proceso, los objetos cooperantes existen y almacenan punteros entre sí. Las figuras siguientes muestran la secuencia en la que se crean los objetos. Puede seguir la secuencia de una figura a una figura.

![Secuencia para crear un documento](../mfc/media/vc387l1.gif "Secuencia para crear un documento") <br/>
Secuencia de creación de un documento

![Secuencia de creación de ventanas de marco](../mfc/media/vc387l2.png "Secuencia de creación de ventanas de marco") <br/>
Secuencia de creación de una ventana de marco

![Secuencia para crear una vista](../mfc/media/vc387l3.gif "Secuencia para crear una vista") <br/>
Secuencia de creación de una vista

Para obtener información sobre cómo el marco de trabajo inicializa los nuevos objetos de documento, vista y ventana de marco, vea las clases [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) en la referencia de biblioteca MFC. Consulte también la [Nota técnica 22](../mfc/tn022-standard-commands-implementation.md), que explica los procesos de creación e inicialización más adelante en su análisis de los comandos estándar del marco de trabajo para los elementos **Nuevo** y **Abrir** en el menú **Archivo.**

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicializar sus propias adiciones a estas clases

Las figuras anteriores también sugieren los puntos en los que puede invalidar las funciones miembro para inicializar los objetos de la aplicación. Una invalidación de la clase de `OnInitialUpdate` vista es el mejor lugar para inicializar la vista. La `OnInitialUpdate` llamada se produce inmediatamente después de crear la ventana de marco y la vista dentro de la ventana de marco se adjunta a su documento. Por ejemplo, si la vista es una `CScrollView` vista `CView`de desplazamiento (derivada de en lugar `OnInitialUpdate` de ), debe establecer el tamaño de la vista en función del tamaño del documento en la invalidación. (Este proceso se describe en la descripción de la clase [CScrollView](../mfc/reference/cscrollview-class.md).) Puede invalidar `CDocument` las `OnNewDocument` funciones miembro y `OnOpenDocument` proporcionar la inicialización específica de la aplicación del documento. Normalmente, debe invalidar ambos, ya que un documento se puede crear de dos maneras.

En la mayoría de los casos, la invalidación debe llamar a la versión de la clase base. Para obtener más información, vea las funciones miembro con nombre de las clases [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), [CFrameWnd](../mfc/reference/cframewnd-class.md)y [CWinApp](../mfc/reference/cwinapp-class.md) en la referencia de biblioteca MFC.

## <a name="see-also"></a>Consulte también

[Plantillas de documento y el proceso de creación de documentos/vistas](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](../mfc/document-template-creation.md)<br/>
[Crear documentos y vistas](../mfc/document-view-creation.md)<br/>
[Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)
