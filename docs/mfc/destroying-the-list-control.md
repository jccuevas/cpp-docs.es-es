---
title: Destruir el control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: 5004026da6bb309cc2c966384724b7b98e254e1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508699"
---
# <a name="destroying-the-list-control"></a>Destruir el control de lista

Si incrusta el objeto [CListCtrl](../mfc/reference/clistctrl-class.md) como un miembro de datos de una vista o una clase de cuadro de diálogo, se destruye cuando se destruye su propietario. Si usa [CListView](../mfc/reference/clistview-class.md), el marco de trabajo destruye el control cuando destruye la vista.

Si organiza los datos de la lista para que se almacenen en la aplicación en lugar de en el control de lista, deberá organizar su desasignación. Para obtener más información, vea [elementos de devolución de llamada y la máscara de devolución de llamada](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Además, usted es responsable de desasignar las listas de imágenes que ha creado y asociado al objeto de control de lista.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
