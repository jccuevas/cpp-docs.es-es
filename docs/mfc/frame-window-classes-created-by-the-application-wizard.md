---
title: Clases de ventana de marco creadas por el Asistente para aplicaciones
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
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
ms.openlocfilehash: c17ba2b6dd79e8e62baa29bba403c136d16a0d95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077535"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Clases de ventana de marco creadas por el Asistente para aplicaciones

Al crear un nuevo proyecto MFC desde el cuadro de diálogo **nuevo proyecto** , además de las clases de aplicación, documento y vista, el Asistente para aplicaciones crea una clase de ventana de marco derivada para la ventana de marco principal de la aplicación. De forma predeterminada, se llama a la clase `CMainFrame` y los archivos que la contienen se denominan MAINFRM. H y MAINFRM. CPP.

Si la aplicación es SDI, la clase `CMainFrame` se deriva de la clase [CFrameWnd](../mfc/reference/cframewnd-class.md).

Si la aplicación es MDI, `CMainFrame` se deriva de la clase [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md). En este caso `CMainFrame` implementa el marco principal, que contiene el menú, la barra de herramientas y las barras de estado. El Asistente para aplicaciones no deriva una nueva clase de ventana de marco de documento. En su lugar, utiliza la implementación predeterminada en la [clase CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md). El marco de trabajo de MFC crea una ventana secundaria que contiene cada vista (que puede ser de tipo `CScrollView`, `CEditView`, `CTreeView`, `CListView`, etc.) que la aplicación requiere. Si necesita personalizar la ventana de marco de documento, puede crear una nueva clase de ventana de marco de documento (vea [Agregar una clase](../ide/adding-a-class-visual-cpp.md)).

Si opta por admitir una barra de herramientas, la clase también tiene variables miembro de tipo [CToolBar](../mfc/reference/ctoolbar-class.md) y [CStatusBar](../mfc/reference/cstatusbar-class.md) y una función de controlador de mensajes `OnCreate` para inicializar las dos [barras de control](../mfc/control-bars.md).

Estas clases de ventana de marco funcionan tal y como se crearon, pero para mejorar su funcionalidad, debe agregar variables de miembro y funciones miembro. También puede hacer que las clases de ventana controlen otros mensajes de Windows. Para obtener más información, vea [cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Consulte también

[Clases de ventana de marco](../mfc/frame-window-classes.md)<br/>
[Archivos de encabezado y código fuente de controles o programas MFC](../build/reference/mfc-program-or-control-source-and-header-files.md)
