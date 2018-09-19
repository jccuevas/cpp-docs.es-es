---
title: Clases de arquitectura de aplicación MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1174a994f345f4b7733e82603b5a49ed8977651
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351435"
---
# <a name="mfc-application-architecture-classes"></a>Clases de arquitectura de aplicaciones MFC
Clases de esta categoría contribuyen a la arquitectura de una aplicación de marco de trabajo. Proporciona funcionalidad común para la mayoría de las aplicaciones. Rellene el marco de trabajo para agregar la funcionalidad específica de la aplicación. Normalmente, para ello, derivar nuevas clases de las clases de arquitectura y, a continuación, agregar los nuevos miembros o reemplazar las funciones miembro existentes.  
  
 [Asistentes para aplicaciones](../mfc/reference/mfc-application-wizard.md) generar diferentes tipos de aplicaciones, que utiliza el marco de aplicación de maneras diferentes. SDI (interfaz de único documento) y las aplicaciones MDI (interfaz de múltiples documentos) hacen un uso completo de una parte de framework llama arquitectura documento/vista. Otros tipos de aplicaciones, como las aplicaciones basadas en el cuadro de diálogo y las aplicaciones basadas en formularios, DLL, utilizan solo algunas de las características de la arquitectura documento/vista.  
  
 Las aplicaciones de documento/vista contienen uno o varios conjuntos de documentos, vistas y ventanas de marco. Un objeto de plantilla de documento asocia las clases para cada conjunto de documento/vista/marco.  
  
 Aunque no es necesario usar la arquitectura documento/vista en la aplicación MFC, hay una serie de ventajas a hacerlo. La MFC OLE contenedor y servidor compatibilidad se basa en la arquitectura documento/vista, como es compatible con vista previa de impresión y.  
  
 Todas las aplicaciones de MFC dispone de al menos dos objetos: un objeto de aplicación se deriva de [CWinApp](../mfc/reference/cwinapp-class.md)y algún tipo de objeto de la ventana principal, derivado (a menudo de manera indirecta) de [CWnd](../mfc/reference/cwnd-class.md). (A menudo, se deriva de la ventana principal [CFrameWnd](../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), o [CDialog](../mfc/reference/cdialog-class.md), todos ellos se derivan `CWnd`.)  
  
 Las aplicaciones que utilizan la arquitectura documento/vista contienen objetos adicionales. Los objetos principales son:  
  
-   Un objeto de aplicación se deriva de la clase [CWinApp](../mfc/reference/cwinapp-class.md), tal y como se mencionó antes.  
  
-   Uno o varios objetos de clase de documento se derivan de la clase [CDocument](../mfc/reference/cdocument-class.md). Objetos de clase de documento son responsables de la representación interna de los datos que se ha manipulado de la vista. Pueden asociarse a un archivo de datos.  
  
-   Uno o varios objetos de vista se derivan de la clase [CView](../mfc/reference/cview-class.md). Cada vista es una ventana que se adjunta a un documento y se asocia con una ventana de marco. Vistas de mostrar y manipulan los datos contenidos en un objeto de clase de documento.  
  
 Las aplicaciones de documento/vista también contienen ventanas de marco (derivado de [CFrameWnd](../mfc/reference/cframewnd-class.md)) y plantillas de documento (derivado de [CDocTemplate](../mfc/reference/cdoctemplate-class.md)).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

