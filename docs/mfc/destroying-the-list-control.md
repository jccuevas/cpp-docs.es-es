---
title: Destruir el Control de lista | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25642357e3dd9117ae2817307ed5fa3c4a0921d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424549"
---
# <a name="destroying-the-list-control"></a>Destruir el control de lista

Si incrusta la [CListCtrl](../mfc/reference/clistctrl-class.md) objeto como un miembro de datos de una clase de vista o cuadro de diálogo, se destruye cuando se destruye su propietario. Si usa un [CListView](../mfc/reference/clistview-class.md), el marco de trabajo destruye el control cuando se destruye la vista.

Si organizas para algunos de los datos de lista que se almacenará en la aplicación en lugar del control de lista, deberá desasignarlos. Para obtener más información, consulte [elementos de devolución de llamada y máscara de devolución de llamada](/windows/desktop/Controls/using-list-view-controls) en el SDK de Windows.

Además, usted es responsable de desasignar las listas de imágenes creado y asociado al objeto de control de lista.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

