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
ms.openlocfilehash: 7a714b5d7ba97c12b7134fa4890bddf5ed095c5b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620561"
---
# <a name="creating-new-documents-windows-and-views"></a>Crear nuevos documentos, ventanas y vistas

Las siguientes figuras proporcionan información general sobre el proceso de creación de documentos, vistas y ventanas de marco. Otros artículos que se centran en los objetos participantes proporcionan más detalles.

Al finalizar este proceso, los objetos cooperativos existen y almacenan los punteros entre sí. Las siguientes figuras muestran la secuencia en la que se crean los objetos. Puede seguir la secuencia de la ilustración a la figura.

![Secuencia para crear un documento](../mfc/media/vc387l1.gif "Secuencia para crear un documento") <br/>
Secuencia de creación de un documento

![Secuencia de creación de ventanas de marco](../mfc/media/vc387l2.png "Secuencia de creación de ventanas de marco") <br/>
Secuencia de creación de una ventana de marco

![Secuencia para crear una vista](../mfc/media/vc387l3.gif "Secuencia para crear una vista") <br/>
Secuencia de creación de una vista

Para obtener información sobre cómo el marco de trabajo inicializa los nuevos objetos de documento, vista y ventana de marco, vea las clases [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)y [CMDIChildWnd](reference/cmdichildwnd-class.md) en la referencia de la biblioteca MFC. Consulte también la [Nota técnica 22](tn022-standard-commands-implementation.md), en la que se explican los procesos de creación e inicialización más adelante en su discusión sobre los comandos estándar del marco para los elementos **nuevos** y **abiertos** en el menú **archivo** .

## <a name="initializing-your-own-additions-to-these-classes"></a><a name="_core_initializing_your_own_additions_to_these_classes"></a>Inicializar sus propias adiciones a estas clases

Las figuras anteriores también sugieren los puntos en los que puede invalidar las funciones miembro para inicializar los objetos de la aplicación. Una invalidación de `OnInitialUpdate` en la clase de vista es el mejor lugar para inicializar la vista. La `OnInitialUpdate` llamada se produce inmediatamente después de crear la ventana de marco y la vista dentro de la ventana de marco se adjunta a su documento. Por ejemplo, si la vista es una vista de desplazamiento (derivada de en `CScrollView` lugar de `CView` ), debe establecer el tamaño de la vista en función del tamaño del documento en la `OnInitialUpdate` invalidación. (Este proceso se describe en la descripción de la clase [CScrollView](reference/cscrollview-class.md)). Puede invalidar las `CDocument` funciones miembro `OnNewDocument` y `OnOpenDocument` proporcionar la inicialización específica de la aplicación del documento. Normalmente, debe reemplazar ambos, ya que un documento se puede crear de dos maneras.

En la mayoría de los casos, la invalidación debe llamar a la versión de la clase base. Para obtener más información, vea las funciones miembro con nombre de las clases [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md), [CFrameWnd](reference/cframewnd-class.md)y [CWINAPP](reference/cwinapp-class.md) en la referencia de la biblioteca MFC.

## <a name="see-also"></a>Consulte también

[Plantillas de documento y el proceso de creación de documentos y vistas](document-templates-and-the-document-view-creation-process.md)<br/>
[Creación de plantillas de documentos](document-template-creation.md)<br/>
[Crear documentos y vistas](document-view-creation.md)<br/>
[Relaciones entre objetos MFC](relationships-among-mfc-objects.md)
