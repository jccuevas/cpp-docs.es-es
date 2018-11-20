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
ms.openlocfilehash: d4b6ccf8a75cc7679f78fba48314073bc53b66a5
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176802"
---
# <a name="managing-mdi-child-windows"></a>Administrar ventanas secundarias MDI

Ventanas de marco principal MDI (una por aplicación) contienen una ventana secundaria especial denominada ventana MDICLIENT. La ventana MDICLIENT administra el área cliente de la ventana de marco principal y tiene ventanas secundarias: las ventanas de documento, que se deriva de `CMDIChildWnd`. Dado que las ventanas de documento son ventanas de marco a sí mismos (ventanas secundarias de MDI), también pueden tener sus propios elementos secundarios. En todos estos casos, la ventana primaria administra sus ventanas secundarias y envía algunos comandos.

En una ventana de marco MDI, la ventana de marco administra la ventana MDICLIENT, cambiar la posición junto con las barras de control. La ventana MDICLIENT, a su vez, administra todas las ventanas de marco secundarias MDI. En la siguiente ilustración muestra la relación entre una ventana marco MDI, su ventana MDICLIENT y sus ventanas de marco de documento secundarias.

![Ventanas secundarias en una ventana marco MDI](../mfc/media/vc37gb1.gif "ventanas secundarias en una ventana marco MDI") <br/>
Ventanas marco de MDI y ventanas secundarias

Una ventana marco MDI también funciona junto con la ventana secundaria MDI actual, si hay alguno. La ventana de marco MDI delega los mensajes de comando al formulario secundario MDI antes de intentar controlar propio.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)

