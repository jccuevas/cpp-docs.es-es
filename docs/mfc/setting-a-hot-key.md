---
title: Establecer una tecla de acceso rápido
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a77aad4881acd04c6dabb6dce90acc01be2cfbc8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307788"
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido

La aplicación puede usar la información proporcionada por una tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) control de dos maneras:

- Configurar una tecla de acceso rápido global para activar una ventana no secundaria mediante el envío de un [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje en la ventana para activarse.

- Configurar una tecla de acceso rápido específicas del subproceso mediante una llamada a la función Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
