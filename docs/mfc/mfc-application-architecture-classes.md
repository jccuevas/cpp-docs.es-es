---
title: Clases de arquitectura de aplicaciones MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 455a49a4f93f2fb2590447071edca76a32cbc5dd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618024"
---
# <a name="mfc-application-architecture-classes"></a>Clases de arquitectura de aplicaciones MFC

Las clases de esta categoría contribuyen a la arquitectura de una aplicación de marco. Proporcionan funcionalidad común a la mayoría de las aplicaciones. Rellene el marco de trabajo para agregar funcionalidad específica de la aplicación. Normalmente, esto se hace derivando nuevas clases de las clases de arquitectura y agregando nuevos miembros o invalidando las funciones miembro existentes.

Los [asistentes para aplicaciones](reference/mfc-application-wizard.md) generan varios tipos de aplicaciones, todas las cuales utilizan el marco de trabajo de la aplicación de maneras diferentes. Las aplicaciones SDI (interfaz de un único documento) y MDI (interfaz de múltiples documentos) hacen un uso completo de una parte del marco de trabajo denominada arquitectura documento/vista. Otros tipos de aplicaciones, como las aplicaciones basadas en cuadros de diálogo, las aplicaciones basadas en formularios y los archivos dll, usan solo algunas de las características de arquitectura de documento/vista.

Las aplicaciones de documento o vista contienen uno o más conjuntos de documentos, vistas y ventanas de marco. Un objeto de plantilla de documento asocia las clases de cada documento, vista o conjunto de Marcos.

Aunque no es necesario utilizar la arquitectura de documento/vista en la aplicación MFC, hay una serie de ventajas para hacerlo. La compatibilidad con el servidor y el contenedor OLE de MFC se basa en la arquitectura de documento/vista, como es la compatibilidad con la impresión y la vista previa de impresión.

Todas las aplicaciones MFC tienen al menos dos objetos: un objeto de aplicación derivado de [CWinApp](reference/cwinapp-class.md)y algún tipo de objeto de ventana principal, derivado (a menudo indirectamente) de [CWnd](reference/cwnd-class.md). (A menudo, la ventana principal se deriva de [CFrameWnd](reference/cframewnd-class.md), [CMDIFrameWnd](reference/cmdiframewnd-class.md)o [CDialog](reference/cdialog-class.md), todas las cuales se derivan de `CWnd` ).

Las aplicaciones que utilizan la arquitectura de documento/vista contienen objetos adicionales. Los objetos de entidad de seguridad son:

- Objeto de aplicación derivado de la clase [CWinApp](reference/cwinapp-class.md), como se mencionó antes.

- Uno o varios objetos de clase de documento derivados de la clase [CDocument](reference/cdocument-class.md). Los objetos de clase de documento son responsables de la representación interna de los datos manipulados en la vista. Pueden estar asociados a un archivo de datos.

- Uno o varios objetos de vista derivados de la clase [CView](reference/cview-class.md). Cada vista es una ventana que se adjunta a un documento y se asocia a una ventana de marco. Las vistas muestran y manipulan los datos contenidos en un objeto de clase de documento.

Las aplicaciones de documento y vista también contienen ventanas de marco (derivadas de [CFrameWnd](reference/cframewnd-class.md)) y plantillas de documento (derivadas de [CDocTemplate](reference/cdoctemplate-class.md)).

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
