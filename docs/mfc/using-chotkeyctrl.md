---
title: Usar CHotKeyCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- keys, hot and CHotKeyCtrl
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
ms.openlocfilehash: e2002d96a1eba913e260fa92281f730355a83ca5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447243"
---
# <a name="using-chotkeyctrl"></a>Usar CHotKeyCtrl

Un control de tecla de acceso rápido, representado por la clase [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), es una ventana que muestra una representación de texto de la combinación de teclas que el usuario escribe en él, como Ctrl + Mayús + Q. También mantiene una representación interna de esta clave en forma de código de tecla virtual y un conjunto de marcas que representan el estado de desplazamiento. En realidad, el control de tecla de acceso rápido no establece la tecla de acceso rápido, lo que hace que sea hasta el programa. (Para obtener una lista de códigos de tecla virtual estándar, vea Winuser. h).

Use un control de tecla de acceso rápido para obtener la entrada de un usuario para la que la tecla de acceso rápido se debe asociar a una ventana o subproceso. Los controles de tecla de acceso rápido se usan a menudo en cuadros de diálogo, como puede mostrar al solicitar al usuario que asigne una tecla de acceso rápido. Es responsabilidad del programa recuperar los valores que describen la tecla de acceso rápido del control de tecla de acceso rápido y llamar a las funciones adecuadas para asociar la tecla de acceso rápido a una ventana o subproceso.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Uso de un control de tecla de acceso directo](../mfc/using-a-hot-key-control.md)

- [Establecimiento de una tecla de acceso directo](../mfc/setting-a-hot-key.md)

- [Teclas de acceso directo globales](../mfc/global-hot-keys.md)

- [Teclas de acceso directo específicas del subproceso](../mfc/thread-specific-hot-keys.md)

## <a name="see-also"></a>Consulte también

[Controles](../mfc/controls-mfc.md)
