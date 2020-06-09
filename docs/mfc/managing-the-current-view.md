---
title: Administrar la vista actual
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], and OnActivateView method [MFC]
- views [MFC], deactivating
- views [MFC], activating
- frame windows [MFC], current view
- OnActivateView method [MFC]
- views [MFC], current
- deactivating views [MFC]
- current view in frame window [MFC]
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
ms.openlocfilehash: d2ce9d77234260ebcb1946dd381264fb6654a91c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621308"
---
# <a name="managing-the-current-view"></a>Administrar la vista actual

Como parte de la implementación predeterminada de ventanas de marco, una ventana de marco realiza un seguimiento de una vista activa actualmente. Si la ventana de marco contiene más de una vista, como por ejemplo en una ventana divisora, la vista actual es la vista más reciente en uso. La vista activa es independiente de la ventana activa de Windows o del foco de entrada actual.

Cuando cambia la vista activa, el marco de trabajo notifica a la vista actual llamando a su función miembro [OnActivateView](reference/cview-class.md#onactivateview) . Puede saber si la vista se está activando o desactivando examinando el `OnActivateView` parámetro *bActivate* de. De forma predeterminada, `OnActivateView` establece el foco en la vista actual en la activación. Puede invalidar `OnActivateView` para realizar cualquier procesamiento especial cuando la vista está desactivada o reactivada. Por ejemplo, puede que desee proporcionar indicaciones visuales especiales para distinguir la vista activa de otras vistas inactivas.

Una ventana de marco reenvía comandos a su vista actual (activa), como se describe en [enrutamiento de comandos](command-routing.md), como parte del enrutamiento de comandos estándar.

## <a name="see-also"></a>Consulte también

[Usar ventanas de marco](using-frame-windows.md)
