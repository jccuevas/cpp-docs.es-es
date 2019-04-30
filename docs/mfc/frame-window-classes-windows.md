---
title: Clases de ventana de marco (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 3e56bd0f449992118db75a44c39b6e0e15cb0d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392798"
---
# <a name="frame-window-classes-windows"></a>Clases de ventana de marco (Windows)

Ventanas de marco son ventanas que una aplicación o una parte de una aplicación de marco. Ventanas de marco suelen contengan otras ventanas, como vistas, barras de herramientas y barras de estado. En el caso de `CMDIFrameWnd`, que pueden contener `CMDIChildWnd` objetos indirectamente.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La clase base para las ventanas de marco de documento de una aplicación MDI.

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
Una ventana de marco de altura media que se suelen ver alrededor de barras de herramientas flotantes.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para obtener una vista cuando se está editando un documento de servidor en su lugar.

## <a name="related-class"></a>Clase relacionada

Clase `CMenu` proporciona una interfaz a través de la que se va a obtener acceso a los menús de la aplicación. Es útil para manipular menús dinámicamente en tiempo de ejecución; Por ejemplo, al agregar o eliminar elementos de menú según el contexto. Aunque los menús se usan más a menudo con ventanas de marco, también puede usar con los cuadros de diálogo y otras ventanas no secundaria.

[CMenu](../mfc/reference/cmenu-class.md)<br/>
Encapsula un `HMENU` identificador de la aplicación de la barra de menús y menús emergentes.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
