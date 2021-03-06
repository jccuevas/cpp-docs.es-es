---
title: Establecer una tecla de acceso rápido
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: 7b49f24039b130f74693e7567f5287476126f225
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511210"
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido

La aplicación puede usar la información proporcionada por un control de tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) de una de estas dos maneras:

- Configure una tecla de acceso rápido global para activar una ventana no secundaria mediante el envío de un mensaje [WM_SETHOTKEY](/windows/win32/inputdev/wm-sethotkey) a la ventana que se va a activar.

- Configure una tecla de acceso rápido específica del subproceso llamando a la función de Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
