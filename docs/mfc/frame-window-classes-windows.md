---
title: Clases de ventana de marco (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 1c0a1e1e93433e0fbe07c11eb350216173e74d84
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625850"
---
# <a name="frame-window-classes-windows"></a>Clases de ventana de marco (Windows)

Las ventanas de marco son ventanas que enmarcan una aplicación o una parte de una aplicación. Las ventanas de marco suelen contener otras ventanas, como vistas, barras de herramientas y barras de estado. En el caso de `CMDIFrameWnd` , pueden contener `CMDIChildWnd` objetos indirectamente.

[CFrameWnd](reference/cframewnd-class.md)<br/>
La clase base para la ventana de marco principal de la aplicación SDI. También es la clase base para todas las demás clases de ventana de marco.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
La clase base para la ventana de marco principal de una aplicación MDI.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
La clase base para las ventanas de marco de documento de una aplicación MDI.

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
Una ventana de marco de ancho medio suele estar visible alrededor de las barras de herramientas flotantes.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para una vista cuando se está editando un documento de servidor en su lugar.

## <a name="related-class"></a>Clase relacionada

`CMenu`La clase proporciona una interfaz a través de la cual se obtiene acceso a los menús de la aplicación. Es útil para manipular los menús dinámicamente en tiempo de ejecución; por ejemplo, al agregar o eliminar elementos de menú según el contexto. Aunque los menús se usan con mayor frecuencia con ventanas de marco, también se pueden usar con cuadros de diálogo y otras ventanas no secundarias.

[CMenu](reference/cmenu-class.md)<br/>
Encapsula un `HMENU` identificador en la barra de menús y los menús emergentes de la aplicación.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
