---
title: Clases de arquitectura de aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 47feeb056d02b81bb88ccf3c5fd49bc983583ee7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277604"
---
# <a name="mfc-application-architecture-classes"></a>Clases de arquitectura de aplicaciones MFC

Las clases en esta categoría contribuyen a la arquitectura de una aplicación de marco de trabajo. Proporcionan funcionalidad común para la mayoría de las aplicaciones. Rellene el marco de trabajo para agregar funcionalidad específica de la aplicación. Normalmente, para ello, derivar clases nuevas de las clases de arquitectura y, a continuación, agregar nuevos miembros o reemplazar las funciones de miembro existentes.

[Asistentes para aplicaciones](../mfc/reference/mfc-application-wizard.md) generar varios tipos de aplicaciones, todas ellas usan el marco de aplicación de maneras diferentes. SDI (interfaz de único documento) y las aplicaciones MDI (interfaz de múltiples documentos) hacen un uso completo de una parte del marco llama a la arquitectura documento/vista. Otros tipos de aplicaciones, como las aplicaciones basadas en el cuadro de diálogo, aplicaciones basadas en formularios y los archivos DLL, utilizan sólo algunas de las características de arquitectura documento/vista.

Las aplicaciones de documento/vista contienen uno o varios conjuntos de documentos, vistas y ventanas de marco. Un objeto de plantilla de documento asocia las clases para cada conjunto de documento/vista/marco.

Aunque no es necesario utilizar la arquitectura documento/vista en la aplicación MFC, hay una serie de ventajas para hacerlo. La OLE de MFC contenedor y servidor compatibilidad se basa en la arquitectura documento/vista, como es la compatibilidad con impresión y vista previa.

Todas las aplicaciones de MFC tienen al menos dos objetos: deriva de un objeto de aplicación [CWinApp](../mfc/reference/cwinapp-class.md)y algún tipo de objeto de ventana principal, (a menudo indirectamente) derivado [CWnd](../mfc/reference/cwnd-class.md). (A menudo, se deriva de la ventana principal [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), o [CDialog](../mfc/reference/cdialog-class.md), todos los cuales se derivan `CWnd`.)

Las aplicaciones que utilizan la arquitectura documento/vista contienen objetos adicionales. Los objetos principales son:

- Un objeto de aplicación deriva de la clase [CWinApp](../mfc/reference/cwinapp-class.md), tal y como se mencionó antes.

- Uno o más objetos de clase de documento derivan de la clase [CDocument](../mfc/reference/cdocument-class.md). Objetos de clase de documento son responsables de la representación interna de los datos que se ha manipulado de la vista. Pueden asociar con un archivo de datos.

- Derivan de uno o más objetos de vista de clase [CView](../mfc/reference/cview-class.md). Cada vista es una ventana que se adjunta a un documento y asociada con una ventana de marco. Vistas de mostrar y manipulan los datos contenidos en un objeto de clase de documento.

Las aplicaciones de documento/vista también contienen ventanas de marco (derivado de [CFrameWnd](../mfc/reference/cframewnd-class.md)) y plantillas de documento (derivado de [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
