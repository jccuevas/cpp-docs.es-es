---
title: Clases de ventana de marco crean por el Asistente para aplicaciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CMainFrame
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3446de072266fdf7661d2e8d8ca0fc968279646
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345057"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Clases de ventana de marco creadas por el Asistente para aplicaciones
Cuando se usa el [Asistente para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md) para crear una aplicación esquema, además de la aplicación, documento y las clases de vista, el Asistente para aplicaciones crea una clase derivada de la ventana de marco de ventana de marco principal de la aplicación. La clase se denomina `CMainFrame` forma predeterminada y los archivos que contienen se denominan MAINFRM. H y MAINFRM. CPP.  
  
 Si la aplicación es SDI, su `CMainFrame` clase se deriva de la clase [CFrameWnd](../mfc/reference/cframewnd-class.md).  
  
 Si la aplicación es MDI, `CMainFrame` se deriva de la clase [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). En este caso `CMainFrame` implementa el marco principal, que contiene las barras de menú, barra de herramientas y el estado. El Asistente para aplicaciones no se deriva una nueva clase de ventana de marco de documento para usted. En su lugar, utiliza la implementación predeterminada de [CMDIChildWnd (clase)](../mfc/reference/cmdichildwnd-class.md). El marco de trabajo MFC crea una ventana secundaria para que contenga cada vista (que puede ser de tipo `CScrollView`, `CEditView`, `CTreeView`, `CListView`, y así sucesivamente) que requiere la aplicación. Si necesita personalizar la ventana de marco de documento, puede crear una nueva clase de ventana de marco de documento (vea [agregar una clase](../ide/adding-a-class-visual-cpp.md)).  
  
 Si decide admitir una barra de herramientas, la clase también tiene las variables de miembro de tipo [CToolBar](../mfc/reference/ctoolbar-class.md) y [CStatusBar](../mfc/reference/cstatusbar-class.md) y `OnCreate` función de controlador de mensajes para inicializar los dos [ las barras de control](../mfc/control-bars.md).  
  
 Estas clases de ventana de marco de trabajo tal como se creó, pero para mejorar su funcionalidad, debe agregar las variables miembro y funciones miembro. También puede hacer que las clases de ventana posible otros mensajes de Windows. Para obtener más información, consulte [cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Clases de ventana de marco](../mfc/frame-window-classes.md)   
 [Archivos de encabezado y código fuente de controles o programas MFC](../ide/mfc-program-or-control-source-and-header-files.md)

