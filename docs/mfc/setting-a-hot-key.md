---
title: Establecer una tecla de acceso rápido
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [MFC], hot keys
- access keys [MFC], hot keys
- CHotKeyCtrl class [MFC], setting hot key
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
ms.openlocfilehash: ebaddb4a64a4d9d47b82fd36f118c74527554e53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893229"
---
# <a name="setting-a-hot-key"></a>Establecer una tecla de acceso rápido

La aplicación puede usar la información proporcionada por una tecla de acceso rápido ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) control de dos maneras:

- Configurar una tecla de acceso rápido global para activar una ventana no secundaria mediante el envío de un [mensaje WM_SETHOTKEY](/windows/desktop/inputdev/wm-sethotkey) mensaje en la ventana para activarse.

- Configurar una tecla de acceso rápido específicas del subproceso mediante una llamada a la función Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey).

## <a name="see-also"></a>Vea también

[Uso de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

