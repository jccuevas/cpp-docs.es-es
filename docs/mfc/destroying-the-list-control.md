---
title: Destruir el control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [MFC], destroying
- CListCtrl class [MFC], destroying controls
ms.assetid: 513ec820-3a02-49d2-b073-a6a7a3fc91b3
ms.openlocfilehash: d128a613a2a4cb595f362f843a5ae2eba830e538
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621902"
---
# <a name="destroying-the-list-control"></a>Destruir el control de lista

Si incrusta el objeto [CListCtrl](reference/clistctrl-class.md) como un miembro de datos de una vista o una clase de cuadro de diálogo, se destruye cuando se destruye su propietario. Si usa [CListView](reference/clistview-class.md), el marco de trabajo destruye el control cuando destruye la vista.

Si organiza los datos de la lista para que se almacenen en la aplicación en lugar de en el control de lista, deberá organizar su desasignación. Para obtener más información, vea [elementos de devolución de llamada y la máscara de devolución de llamada](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Además, usted es responsable de desasignar las listas de imágenes que ha creado y asociado al objeto de control de lista.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
