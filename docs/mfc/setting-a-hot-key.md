---
title: Establecer una tecla de acceso rápido
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: a5dc885767137a4e53d1ea0d066944d5f276c38c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508802"
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido

La aplicación puede usar la información proporcionada por una tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) control de dos maneras:

- Configurar una tecla de acceso rápido global para activar una ventana no secundaria mediante el envío de un [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje en la ventana para activarse.

- Configurar una tecla de acceso rápido específicas del subproceso mediante una llamada a la función Windows [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

