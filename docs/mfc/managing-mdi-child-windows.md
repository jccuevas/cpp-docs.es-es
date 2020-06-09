---
title: Administrar ventanas secundarias MDI
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: 6e8e3d0aa51eeea112597485a9221dcba4feda87
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618358"
---
# <a name="managing-mdi-child-windows"></a>Administrar ventanas secundarias MDI

Las ventanas de marco principal MDI (una por aplicación) contienen una ventana secundaria especial denominada ventana MDICLIENT. La ventana MDICLIENT administra el área cliente de la ventana de marco principal y tiene ventanas secundarias: las ventanas de documento, derivadas de `CMDIChildWnd` . Dado que las ventanas de documento son ventanas de marco (ventanas secundarias MDI), también pueden tener sus propios elementos secundarios. En todos estos casos, la ventana primaria administra sus ventanas secundarias y reenvía algunos comandos a ellas.

En una ventana de marco MDI, la ventana de marco administra la ventana MDICLIENT y la coloca junto con las barras de control. La ventana MDICLIENT, a su vez, administra todas las ventanas de marco secundarias MDI. En la siguiente ilustración se muestra la relación entre una ventana de marco MDI, su ventana MDICLIENT y sus ventanas de marco de documento secundarias.

![Ventanas secundarias en una ventana de marco MDI](../mfc/media/vc37gb1.gif "Ventanas secundarias en una ventana de marco MDI") <br/>
Ventanas marco de MDI y ventanas secundarias

Una ventana de marco MDI también funciona junto con la ventana secundaria MDI actual, si hay alguna. La ventana de marco MDI delega los mensajes de comandos en el elemento secundario MDI antes de intentar controlarlos.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](creating-document-frame-windows.md)

- [Estilos de ventana de marco](frame-window-styles-cpp.md)

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
